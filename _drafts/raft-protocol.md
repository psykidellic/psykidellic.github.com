---
layout: post
title: RAFT Protocol
---
gcloud config configurations list

Start Flask 3

You will need service account/file to access anything starting with services. https://cloud.google.com/docs/authentication/getting-started

source "$(brew --prefix)/Caskroom/google-cloud-sdk/latest/google-cloud-sdk/path.zsh.inc"

https://formulae.brew.sh/cask/google-cloud-sdk

You will also need the google datastore emulator which you can start with

```
gcloud beta emulators datastore start
export DATASTORE_EMULATOR_HOST=localhost:8081
```

And in the window where you are starting Flask, export the environment variable along with the service key environment.

