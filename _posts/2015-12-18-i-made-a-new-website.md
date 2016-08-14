---
layout: article
title: "Look, I Made a New Website!"
modified: 2015-12-28T12:30:00+00:00
categories: blog
subcategory: web
tags: [Jekyll, EC2, rsync, Site Deployment]
image:
  feature: mad-scientist-feature.jpg
  teaser: mad-scientist-teaser.jpg
  credit: Kit
  creditlink: https://www.flickr.com/photos/practicalowl/392894653/
---

After much tinkering, I've finally decided to replace my [Wordpress][w] site with a brand-spanking new static version generated in [Jekyll][j].

The [Jekyll][j] installation currently lives on an [Amazon EC2][ec2] instance so that I can rebuild it from anywhere, but if EC2 starts costing too much money, I'll probably configure it on one of my Macs instead.

I generally use a [shell script][sh] to deploy the site; first, it does a Jekyll build, then it uses rsync to transfer the files from EC2 to Dreamhost via ssh/sftp. It took a little bit to figure out how to get ssh keys set up on both so that rsync wouldn't prompt for a password, but in the end it all came down to [file permissions][p]. I've also configured [Rake][r] so that I can test my build with [html_proofer][h] and deploy the site using my Rakefile.

The coolest part? Thanks to Panic's [Coda for iOS][c], I can deploy the whole thing from my iPhone - start to finish!

The current template is called [Skinny Bones][s]. I've tweaked it a little bit here and there, but it's mostly the same.

An archival version of my old site currently lives on at [old.unsquare.com][o]. I've only ported over a selection of my old posts, and I may eventually take the old site down completely.

[w]: http://wordpress.org
[j]: http://jekyllrb.com
[ec2]: http://aws.amazon.com/ec2/
[sh]: https://www.basbarten.nl/jekyll-deployment/2015/a-simple-shell-script-for-deployment/
[p]: http://wiki.dreamhost.com/Ssh#If_ssh-copy-id_does_not_work
[c]: https://panic.com/coda-ios/
[s]: http://mmistakes.github.io/skinny-bones-jekyll/
[o]: http://old.unsquare.com
[r]: https://github.com/ruby/rake
[h]: https://github.com/gjtorikian/html-proofer