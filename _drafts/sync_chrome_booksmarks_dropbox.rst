---
categories: personal
date: 2012/01/03 21:36:00
title: Devise....
---

 had to add delete method for session http://stackoverflow.com/questions/6557311/no-route-matches-users-sign-out-devise-rails-3
 error flash were not coming http://stackoverflow.com/questions/4635986/rails-devise-error-messages-when-signing-in
 http://stackoverflow.com/questions/4101641/rails-devise-handling-devise-error-

Ritesh-Nadhanis-iMac:playingtalents riteshn$ gem install ruby-debug
Fetching: columnize-0.3.6.gem (100%)
Fetching: rbx-require-relative-0.0.5.gem (100%)
ERROR:  Error installing ruby-debug:
	rbx-require-relative requires Ruby version ~> 1.8.7.

http://stackoverflow.com/questions/7362173/integrating-facebook-login-with-omniauth-on-rails

spend time on     #   user
    if @user.persisted?
      flash[:notice] = I18n.t "devise.omniauth_callbacks.success", :kind => "Facebook"
      sign_in_and_redirect @user, :event => :authentication
    else
      session["devise.facebook_data"] = env["omniauth.auth"]
      redirect_to new_user_registration_url
    end

 https://gist.github.com/1331533

Had to look around FriendlyId which seemed to be little different from devise_for.
>> turned out i was accessing the wrong dictionary value.

>> form. tried to use simple_form. Didnt work - so went back to normal ones.


http://stackoverflow.com/questions/3774916/no-method-error-in-rails-3-app
https://gist.github.com/1205828 - move to bootstrap

class Comment < ActiveRecord::Base
  include ActsAsCommentable::Comment

  belongs_to :commentable, :polymorphic => true

  default_scope :order => 'created_at DESC'

  ...

  default_scope was misunderstood.


http://www.railstoolkit.com/posts/fancyupload-amazon-s3-uploader-with-paperclip

change nested to inline in simple_form

        // enable the upload button.
        uploader.bind('FilesAdded', function(up, files) {
          // start the uploader after the progress bar shows
          // but before that we change the content type. Unfortunately, S3
          // will return the same content type that you set. So image/ is asked
          // to be downloaded rather then just show. So we update the settings dynamically.
          var old_ct = uploader.settings.multipart_params['Content-Type']
          uploader.settings.multipart_params['Content-Type'] = old_ct + files[0].name.split('.')[1];
          alert(uploader.settings.multipart_params['Content-Type']);
          $('#attachment_progress').show('fast', function () {
            uploader.start();
          });
        });

This is for my posterity

You can start nginx automatically on login running as your user with:
  mkdir -p ~/Library/LaunchAgents
  cp /usr/local/Cellar/nginx/1.0.11/org.nginx.nginx.plist ~/Library/LaunchAgents/
  launchctl load -w ~/Library/LaunchAgents/org.nginx.nginx.plist

 /usr/local/etc/nginx/nginx.conf

1	$ dscacheutil -flushcache

... after updating /etc/hosts

nginx: the configuration file /usr/local/etc/nginx/nginx.conf syntax is ok
nginx: [alert] Unable to start the Phusion Passenger watchdog because its executable (/Users/riteshn/.rvm/gems/ruby-1.9.3-rc1/gems/passenger-3.0.0.pre4/agents/PassengerWatchdog) does not exist. This probably means that your Phusion Passenger installation is broken or incomplete, or that your 'passenger_root' directive is set to the wrong value. Please reinstall Phusion Passenger or fix your 'passenger_root' directive, whichever is applicable. (-1: Unknown error)
nginx: configuration file /usr/local/etc/nginx/nginx.conf test is successful


>>>

-prefix=/usr/local/Cellar/nginx/1.0.11 --with-http_ssl_module --with-pcre --conf-path=/usr/local/etc/nginx/

cd /tmp
tar xzvf /usr/local/Cellar/Homebew/nginx-VERSION.tar.gz

Where is your Nginx source code located?

Please specify the directory: /tmp/nginx-1.0.11

--------------------------------------------

Where do you want to install Nginx to?

Please specify a prefix directory [/opt/nginx]: /usr/local/Cellar/nginx/1.0.11

--------------------------------------------

Extra Nginx configure options

If you want to pass extra arguments to the Nginx 'configure' script, then
please specify them. If not, then specify nothing and press Enter.

If you specify nothing then the 'configure' script will be run as follows:

  sh ./configure --prefix='/usr/local/Cellar/nginx/1.0.11' --with-http_ssl_module --add-module='/Users/riteshn/.rvm/gems/ruby-1.9.3-rc1/gems/passenger-3.0.0.pre4/ext/nginx'

Extra arguments to pass to configure script: --conf-path=/usr/local/etc/nginx/

source: /tmp/nginx-1.0.11

prefix=/usr/local/Cellar/nginx/1.0.11 --with-http_ssl_module --with-pcre --conf-path=/usr/local/etc/nginx/
 - i had t specially add nginx.conf in the end


 sudo kill `cat /usr/local/Cellar/nginx/1.0.11/logs/nginx.pid`


 http://groups.google.com/group/phusion-passenger/browse_thread/thread/a440c5a2dbced8?pli=1


  # ps -ef|grep nginx
 root      1911     1  0 18:00 ?        00:00:00 nginx: master process /usr/sbin/nginx
 www-data  1912  1911  0 18:00 ?        00:00:00 nginx: worker process
Lastly, tell nginx to reload the configuration and restart the worker processes:

 # kill -HUP 1911


 >>>>


Download Eclipse
Download the tar,gz and copy eclipse folder to Applications.
Download and update the ADT as mentioned in : http://developer.android.com/sdk/eclipse-adt.html#installing
After the installation restart and it will ask you to download the SDK. For start I selected 2.1 only.
Create android virtual device- Window -> AVD Manager ->


>>>

Git checkout and whitespace magic that cliff showed. Create correct exampole where previous white space is gone and you dont see it.

So you can use git checkout -p

then show git add -p

>>>

brew install sshfs
==> make install
ln: fuse_version.h: Permission denied
Error: The linking step did not complete successfully
The formula built, but is not symlinked into /usr/local
You can try again using `brew link fuse4x'

Ritesh-Nadhanis-iMac:src riteshn$ brew info fuse4x-kext
fuse4x-kext 0.8.14
http://fuse4x.org/
/usr/local/Cellar/fuse4x-kext/0.8.14 (7 files, 312K)

In order for FUSE-based filesystems to work, the fuse4x kernel extension
must be installed by the root user:

  sudo cp -rfX /usr/local/Cellar/fuse4x-kext/0.8.14/Library/Extensions/fuse4x.kext /System/Library/Extensions
  sudo chmod +s /System/Library/Extensions/fuse4x.kext/Support/load_fuse4x

If upgrading from a previous version of Fuse4x, the old kernel extension
will need to be unloaded before performing the steps listed above. First,
check that no FUSE-based filesystems are running:

  mount | grep fuse4x

Unmount all FUSE filesystems and then unload the kernel extension:

  sudo kextunload -b org.fuse4x.kext.fuse4x


http://github.com/mxcl/homebrew/commits/master/Library/Formula/fuse4x-kext.rb


