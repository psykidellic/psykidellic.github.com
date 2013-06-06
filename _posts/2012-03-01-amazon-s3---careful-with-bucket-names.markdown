---
layout: post
title: Amazon S3 bucket names - be very careful
tags: [s3]
---
As I am doing bunch of AWS related work, I create multiple buckets for testing purposes. Today, I created a bucket and by mistake chose the wrong region. Region matters as Paperclip generates the attachment url based on **s3_host_name**. If you access the S3 item with a different starting hostname, Amazon will give you redirection notice.

After realising my mistake, I dropped the bucket and tried to create another one with the same name (using the correct region) and I get:

> A conflicting conditional operation is currently in progress against this resource. Please try again.

The official reply from Amazon is:

> I strongly recommend against deleting a bucket that you want to keep. There's never any guarantee that you will be able to create a new bucket with the same bucket name.

(taken from [https://forums.aws.amazon.com/thread.jspa?threadID=37532]())

Luckily, this was bucket which I was going to use for testing so the name really didnt matter but if it was something for production, things could have gotten hairy.
