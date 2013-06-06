---
layout: post
title: "rvm, Rails 3.1, capistrano, Amazon EC2 - my first basic capistrano deployment script"
tags: [scripts]
---
Even though we are still using Rails 2.x at work, I have been looking into Rails 3.1 for my personal projects and for learning Ruby and Rails. I have been using Rails for 6 months now but never had to write my own deployment script for a Rails app (I have used Fabric for previous Python projects) so this was my opportunity to learn it.

Recently, I registered for my personal account with EC2 which allows me to play with a free micro-instance for a year. Using one of the standard AMIs from [Ubuntu Cloud Images](http://cloud-images.ubuntu.com/releases/11.10/release/), I setup a simple one app server using rvm, Rails 3.1, Passenger and nginx.

>> The ubuntu official AMIs create a basic server with ubuntu user. It seems the convention is to use /var/www/appname to put your
>> application code but for simplicity I will just use the standard /home/ubuntu and /home/ubuntu/appname.
>> More info at

As is always the case with new tools, after reading upon the basic documentation on [Starting Up](https://github.com/capistrano/capistrano/wiki/2.x-Getting-Started) and [Tutorial](https://github.com/capistrano/capistrano/wiki/2.x-From-The-Beginning). Then a quick Googling to check if somebody has written a similar tutorial/basic script. Within two minutes, I come across [Artem's Post](http://www.aaginskiy.com/technology/2011/02/deploying-rails-3-apps-with-capistrano/). Not exactly similar but similar enough.


Taking inspiration from it, my first iteration:

{% highlight ruby %}
require 'bundler/capistrano'
default_run_options[:pty] = true

set :application, "myapp"
set :user, "ubuntu"
set :repository,  "git@bitbucket.org:psykidellic/myapp.git"
set :applicationdir, "/home/ubuntu/myapp"
set :domain, "EC2-IPADDRESS"

#Repo and deploy strategy options
set :scm, :git
set :branch, "master"
#Deploy config
#Keep a local git repo on the server you’re deploying to and simply run a fetch
#from that rather than an entire clone
set :deploy_via, :remote_cache
set :deploy_to, applicationdir

#ssh option. Right now, I am just using my devel machine key to deploy.
#Ideally, it should be own user. A good approach would be the same user for deployment
#and checkout.
ssh_options[:forward_agent] = true

#Since we have only one for now, use the more compressed server syntax.
#generally you set up roles.
server domain, :app, :web, :db, :primary => true
# role :app, :domain
# role :web, :domain
# role :db, :domain, :primary => true

# if you're still using the script/reaper helper you will need
# these http://github.com/rails/irs_process_scripts

# If you are using Passenger mod_rails uncomment this:
namespace :deploy do
  task :start do ; end
  task :stop do ; end
  task :restart, :roles => :app, :except => { :no_release => true } do
    run "#{try_sudo} touch #{File.join(current_path,'tmp','restart.txt')}"
  end
end
{% endhighlight %}

Pretty easy. First round didnt work as it was asking for the user password. But using the normal security settings, ubuntu user does not have a password. This means we need to add our private key to our ssh-agent.

Ooops, need to add the EC2 private key to our agent. We can do this in two ways: a) ssh-add ~/YOUR_PATH_TO_KEY or b) add a option like:

> ssh_options\[:keys\] = \[File.join(ENV\[\"HOME\"], \".ec2\", \"EC2_KEY\")\]

Second iteration, I get as described at [this StackOverflow post](http://stackoverflow.com/questions/6310086/capistrano-git-deployment-could-not-create-work-tree-dir-permission-denied). I just chose to add:

> set :use_sudo, false

**NOTE: In my case since the folders were already created in the setup path using root, I changed the ownership manually. You have been forwarned so don't do it.**

Third iteration,

> sh: bundle: command not found

which means that the environment was not able to get the correct Ruby environment. I use rvm and a global Ruby version on my system. You just need to [read the document](https://rvm.beginrescueend.com/integration/capistrano/) and add the relevant lines.

{% highlight console %}
> cap deploy
> #thats it
{% endhighlight %}

**CAUTION:** This will not restart the nginx server. So as an added convenience, I just add to the file:

> after "deploy", "deploy:restart"

Also, you will have to update nginx.conf to point to current folder as

{% highlight ruby %}
set :deploy_via, :remote_cache
{% endhighlight %}

sets it up to do a fast checkout in a separate folder and can handle errors (if any).

So my final script, that works for me.

{% highlight ruby %}
require 'bundler/capistrano'
default_run_options[:pty] = true

#RVM specific stuff. Taken from: https://rvm.beginrescueend.com/integration/capistrano/
$:.unshift(File.expand_path('./lib', ENV['rvm_path'])) # Add RVM's lib directory to the load path.
require "rvm/capistrano"                  # Load RVM's capistrano plugin.
set :rvm_ruby_string, '1.9.2'        # Or whatever env you want it to run in.



of www.quietewrite.com, http://writer.bighugelabs.com and Write Space
set :application, "appname"
set :user, "ubuntu"
set :repository,  "git@bitbucket.org:psykidellic/appname.git"
set :applicationdir, "/home/ubuntu/appname"
set :domain, "YOUR_HOST_OR_IP"
set :use_sudo, false

#Repo and deploy strategy options
set :scm, :git
set :branch, "master"
#Deploy config
#Keep a local git repo on the server you’re deploying to and simply run a fetch
#from that rather than an entire clone
set :deploy_via, :remote_cache
set :deploy_to, applicationdir

#ssh option. Right now, I am just using my devel machine key to deploy.
#Ideally, it should be own user. A good approach would be the same user for deployment
#and checkout.
ssh_options[:keys] = [File.join(ENV["HOME"], ".ec2", "EC2_KEY")]
ssh_options[:forward_agent] = true

#Since we have only one for now, use the more compressed server syntax.
#generally you set up roles.
server domain, :app, :web, :db, :primary => true
# role :app, :domain
# role :web, :domain
# role :db, :domain, :primary => true

# if you're still using the script/reaper helper you will need
# these http://github.com/rails/irs_process_scripts

# If you are using Passenger mod_rails uncomment this:
namespace :deploy do
  task :start do ; end
  task :stop do ; end
  task :restart, :roles => :app, :except => { :no_release => true } do
    run "#{try_sudo} touch #{File.join(current_path,'tmp','restart.txt')}"
  end
end

after "deploy", "deploy:restart"
{% endhighlight %}
