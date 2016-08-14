---
layout: article
title: "How to Turn Wordpress Into a Static Site Using AMPPS and Simply Static"
category: blog
subcategory: web
tags: [Wordpress, Jekyll, AMPPS, MAMP, static site, shared hosting, dedicated server]
image:
  feature: coding-feature.jpg
  teaser: coding-teaser.jpg
  position: right
date: 2016-01-23T19:42:51+00:00
---

After much tinkering, I *finally* figured out how to make a decent static backup of my [old Wordpress site][o]. I kept running into problems no matter my approach - whether I tried the web interface or [wget][w] - but I had a brainstorm recently that solved a lot of my issues.

The main problem with trying to create a backup in the Wordpress web interface is that my site is on [shared hosting][d] and Wordpress is a resource hog. It's one of the reasons I wanted to switch to [Jekyll][j] in the first place. I'm unlikely to ever be able to afford dedicated hosting, so switching to a static site was definitely an economic choice.

It's also just a matter of impatience. If you try to do anything involved in Wordpress on shared hosting, you'll probably hit the upper limit of your server's memory and your site will crap out.

That's what happened every time I tried to generate a static copy of my site with a plugin called [Simply Static][s]. The plugin would load for a few long minutes and then return an error message.

As for wget, it might just be too convoluted for my purposes. I could never quite figure out the right combination of options to download my site without also downloading a bunch of unnecessary garbage. It was also a pretty slow process. Whenever I inevitably realized halfway through that I'd included the wrong options, it meant I had to start over from the beginning.

My brainstorm was when I realizes that I could use [AMPPS][a] (or [MAMP][m], if you prefer) to create my own dedicated server. See, I really only need the server for as long as it takes to spit out a static copy, so it would be absurd to pay for hosting.<!-- more -->

Here is the process that I used:

1. Download a copy of your Wordpress installation using an FTP program.
2. Log in to your site's PHPMyAdmin and export a copy of your Wordpress MySQL database.
3. Install [AMPPS][a] or [MAMP][m] on your local system. I used AMPSS, so I'll provide instructions for that app, but MAMP has a lot of the same features.
4. Open AMPPS and go into the PHP settings, then select the PHP Extension option. Check the box next to **zip.so**, which is required to use the Simply Static Plugin. It won't hurt if you also change your PHP version to 5.6.
5. Now, start Apache and MySQL in AMPPS.
6. Click the house icon in AMPPS to open the AMPPS dashboard, then go to **Add Domain** and create a record for your domain.
	- One of the nice things about AMPPS is that if you create a record for an existing domain, AMPPS can update your [hosts file][h] so that your browser loads the local copy instead of the live site. However, once you're done with this process, you will need to remove the domain from AMPPS to reset your hosts file.
	- If you want to use a fake domain like **your-site-url.dev**, keep in mind that you will need to [change the site url in your wp-config file][c] to make it work.
7. Copy your Wordpress installation into the folder AMPPS created for your domain.
8. Return to AMPPS and open PHPMyAdmin. Create a new MySQL database, then use the **Import** option to upload the copy of your Wordpress database you downloaded.
9. Update your local wp-config file to reflect the AMPPS MySQL login information, which is available under **MySQL Password** in AMPPS. You'll also need to use localhost as your MySQL server.
10. Open the domain you created in a web browser. If everything went to plan, you should be viewing a locally-running copy of your Wordpress site.
11. Log in to your local site's Wordpress admin.
12. Deactivate all Wordpress plugins that don't provide a required feature.
13. Remove the meta widget and/or any login links anywhere on your theme.
14. Install and activate a plugin that disables your RSS feeds. I found one called [Disable Feeds][d].
15. Install and activate a plugin that generates a static copy of your site. There are a few different plugins available, but the one that worked best for me was [Simply Static][s].
16. If you're feeling super-diligent, go through all of your posts with a fine-toothed comb and find all of the broken video embeds from ten years ago, weird code that relies on long-forgotten plugins, etc. I've done this in fits and starts but I have a loooong way to go before all of those old posts are actually fixed.
17. Now, open the Simply Static settings and confirm that everything is configured correctly. If you're moving your static site to a new domain, you can specify that in the settings.
18. Choose the Generate option, then sit back and wait. Once Simply Static is done, you'll have the option of downloading a zipped copy of the static files.
19. Extract the zipped files and upload them wherever you want your static site to live.
20. Open your new static domain to confirm that everything is working properly. Once you're sure the static site looks the way you want it, remove any local versions of your site from AMPPS and you're good to go!

Although I was able to create a copy of my site using this process, I'd still like to go through old posts and fix broken embeds and links before I say it's completely done. That will probably take a while, just because I hate looking at my posts from so long ago.

[d]: http://dreamhost.com
[j]: http://jekyllrb.com
[o]: http://old.unsquare.com
[w]: https://en.wikipedia.org/wiki/Wget
[s]: https://wordpress.org/plugins/simply-static/
[d]: https://wordpress.org/plugins/disable-feeds/
[a]: http://www.ampps.com
[m]: https://www.mamp.info/en/
[c]: https://codex.wordpress.org/Changing_The_Site_URL
[h]: https://en.wikipedia.org/wiki/Hosts_(file)