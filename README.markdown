## Welcome to the backstage

This is the code repository for my personal website
[fzero.ca](http://fzero.ca). I'm using [Octopress](http://octopress.org)
as my blogging engine, and since all content is public, I don't see any
reason not to publish the source code to GitHub.

### A few interesting things

At its core, this is simply an Octopress blog. There are a few tweaks
here and there that might be of general interest, such as posts being
created automatically as drafts (see `Rakefile`). I also tend to keep one
or more parallel branches to try new designs and features.

But probably the most interesting "feature" is that this blog originally
ran on [Wordpress](http://wordpress.org) on the same domain, so this
hopefully will help other people who are thinking about migrating. The
presence of the original `wp-content/uploads` folder inside `/source`
ensures all content uploaded on Wordpress will still be present for the
migrated posts.

The most important thing to understand is that *everything* under `/source`
will be re-created (and converted from Markdown, if necessary) in the same place on `/public`, 
and the *only* thing that's published to your server is `/public`. 
This is true for things like `.htaccess` too, so that's where you'll put everything.

### Speaking of migration...

I stumbled on a bug that halted the migration process halfway through,
using the [Wordpress.com method](https://github.com/fzero/jekyll/wiki/Blog-Migrations).
This bug actually comes from [Jekyll](http://jekyllrb.com/), the gem upon
which Octopress is based. My [Jekyll fork](https://github.com/fzero/jekyll) already has the fix applied; 
check the [wordpressdotcom.rb](https://github.com/fzero/jekyll/blob/master/lib/jekyll/migrators/wordpressdotcom.rb) 
migration script for more details.

**UPDATE:** My patch has been added to the official Jekyll repo. :-)

### Where things used to be

I used to publish quite a few photo posts using
[Posterous](http://posterous.com), closely emulating
[Tumblr](http://tumblr.com)'s behavior. Posterous connected to my
Wordpress installation via XML-RPC and pushed the posts directly to my
blog. This made me lazy about actually _writing_ posts. It also was a poor
alternative to Instagram (which I left) or Flickr
(which I came back to).

So, in an effort to clean things up, I tweaked my `.htaccess` so all
permalinks to photoposts redirect to the original version on [my
Posterous](http://fzero.posterous.com), which allowed me to keep only
posts with "real" content on my main domain.

### This is a work in progress!

I'm still using the default Octopress theme, but I plan to change that
soon. I will document the theme creation process on the blog
itself.
