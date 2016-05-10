---
layout: post
title: "Cracking FaceBook Instant Articles With Jekyll - RSS Feed"
date: "2016-05-10 10:00:00 +0600"
comments: true
show_meta: true
description: "Instant Articles RSS Feed are not supported by Jekyll - yet! But no worries, I have done this and I am going to share how! :)"
tag:
    - Facebook
    - Jekyll
    - RSS
    - Development
---
Hello All,
Recently I got access to Instant Articles from Facebook for my Jekyll based blog. The interesting part is that as far as I know, Instant Articles RSS Feed are not supported by Jekyll - yet! But no worries, I have done this and I am going to share how :)

<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/en_US/sdk.js#xfbml=1&version=v2.6&appId=394590333892568";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>

<div class="fb-post" data-href="https://www.facebook.com/AmitPublic/photos/a.498726470144373.132061.283932261623796/1323428384340840/?type=3&amp;theater" data-width="500" data-show-text="true"><div class="fb-xfbml-parse-ignore"><blockquote cite="https://www.facebook.com/AmitPublic/posts/1323428384340840:0"><p>Ladies and gentlemen, Instant Articles approval from Facebook :) That means you can get access to my contents even...</p>Posted by <a href="https://www.facebook.com/AmitPublic/">Amit Seal Ami</a> on&nbsp;<a href="https://www.facebook.com/AmitPublic/posts/1323428384340840:0">Tuesday, May 3, 2016</a></blockquote></div></div>
<br />
<!-- more -->
To do this, you need to submit 10 articles which uses Facebook specified Markup tags in your post. An easy way to achieve this is to format your [RSS feed](https://developers.facebook.com/docs/instant-articles/publishing/setup-rss-feed/), and then ingest it.

Problem was, noone did this for Jekyll. At least not as far as I was concerned. And I was just starting with Jekyll as well with zero knowledge about Ruby! Therefore, I had to get my hands dirty. I had to ensure the following:

- The images are surrounded by Figure tags
- The rss items are configured to contain the necessary tags Facebook is looking for

For the first one, I used liquid Figure tags. You can get those in jekyll-figure gem.
For the second one, I created a new file called `instantfeed.xml` and then I included the following:

<script src="https://gist.github.com/lordamit/4bbde7c11e1daafa8e081643787db4a2.js"></script>

Now, your of course need to

- Modify the parts that were specifically written for my blog
- insert yoursite.com/instantfeed.xml to the facebook instant article RSS ingestion section
- build your jekyll site and push it

The RSS should be enough for most of your articles, if not all. Just make sure that you follow the Facebook Instant Articles Design Policies, and you are good to go.
