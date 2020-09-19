---
layout: post
title: Google Cloud SDK
date: 2020-09-18 23:48 -0800
---

I always forget how or which method I use to setup google cloud on a new setup. Noting it down this time to be able to refer back to it. Install using:

```
brew cask install google-cloud-sdk
```

The important output of

```
==> Linking Binary 'bq' to '/usr/local/bin/bq'.
==> Linking Binary 'docker-credential-gcloud' to '/usr/local/bin/docker-credential-gcloud'.
==> Linking Binary 'gcloud' to '/usr/local/bin/gcloud'.
==> Linking Binary 'git-credential-gcloud.sh' to '/usr/local/bin/git-credential-gcloud.sh'.
==> Linking Binary 'gsutil' to '/usr/local/bin/gsutil'.
```

Some useful starter commands

```
glcoud auth list # i have multiple projects from different email list all
gcloud auth login # login to a new one
gcloud projects list # all projects from current setup auth/account
gcloud config configurations list 
gcloud config configurations create `AUTHNAME`
gcloud projects list
```

One of the weird thing I found was when you change an account e.g you want to see all the projects in the account, it also sets the current configuration account to that too (even though you dont want it).

E.g.

```
# Get auth list
gcloud auth list
     Credentialed Accounts
ACTIVE  ACCOUNT
        first@gmail.com
*       second@gmail.com

# Get configuration list
gcloud config configurations list
NAME       IS_ACTIVE  ACCOUNT            PROJECT           COMPUTE_DEFAULT_ZONE  COMPUTE_DEFAULT_REGION
default    False      second@gmail.com  
k8s-learn  True       second@gmail.com  

# Change to first one
gcloud config set account first@gmail.com

NAME       IS_ACTIVE  ACCOUNT            PROJECT           COMPUTE_DEFAULT_ZONE  COMPUTE_DEFAULT_REGION
default    False      second@gmail.com  
k8s-learn  True       first@gmail.com  
```

Even though I dont want to change the account of k8s-learn.

So I just manually edit the configuration files but how do you guys handle it?
