# Hadageto Blog Documentation #

## Technical ##

The blog uses [Hugo](https://gohugo.io) to generate a static site from a bunch of Markdown files.

We use Gitlab's CI mechanism to run Hugo on their server and publish it to their Pages, for free.

## How To... ##

### Create a new blog post ###

Hugo posts are markdown files, in the directory structure that the site has. So, to create a new "tech" post, create a new `article_name.md` file in the `tech` subdirectory.

Each file needs some "Front Matter" - which looks like:

```
+++
title = "Post Title"
description = "Post Description, can be long, gets used as subtitle"
date = "2020-03-24T15:35:54+01:00" ## set this to the future to hold publishing it until then
draft = false ## set this to true to make it publish, false to skip publishing it
categories = ["tech","posts"] ## the categories that this post belongs to
tags = ["tag name", "you can make your own up","literally anything"] ## the tags that this post should have
slug = "your-article" ## the "breadcrumb" slug (e.g. /hadageto-blog/posts/your-article)
+++
```

This has to be at the top of the file, and precede any content. See any other published article for copy/paste.

Images are included using an `img` shortcode, which looks like:

```
{{<img src="/imge-name.jpg" title="Bold title for the image" caption="non-bolded caption, usually used for image attribution" alt="remember to add a text description of the image">}}
```
The image *must* be in the `/static` directory for this to work. You can create subdirectories, but make sure the `img` src reflects this.

### Publish the blog ###

This could not be simpler. Make sure you're in the root of the repo, and on the master branch, and:

```
git add .
git commit -m "made some changes"
git push
```
that's it. The gitlab CI mechanism will pick up the commit to master and do the rest. The blog will update in the next couple of minutes.

### Alter a post ###

Just make the changes to the .md file for the post. Then publish it. You're done.

### Remove a post ###

Either set the Front Matter `draft` field to "true" in the post's .md file, or delete the .md file.


