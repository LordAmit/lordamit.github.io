---
layout: post
title: "Showing Bangla properly in Atom Editor"
date: "2016-05-03 15:22:00 +0600"
comments: true
show_meta: true
description: "Atom Text Editor could not display Bangla font properly in Markdown. I modified the style sheet to specify a font just for Bangla characters. Take a look!"
tag:
    - css
    - atom-text-editor
    - Ubuntu
    - Atom
    - Bengali
    - Bangla
    - Markdown
published: true
imagefeature: "http://i.giphy.com/WlXFkMCUe84Za.gif"
---
Atom editor could not display Bangla font properly in Markdown file. If I changed the font from settings, it was being applied to all characters, and it was messing up the display. However, there is a CSS based style file that can be used to modify the UI of Atom. I just had to edit it to:

- Specify a Bengali font for Bengali Characters only
- Specify a font for All Characters

Only for markdown format, mind you.

{% figure caption:"Before and After effect of modifying style sheet" %}
![Before and After effect of modifying style sheet](http://i.giphy.com/WlXFkMCUe84Za.gif)
{% endfigure %}

I modified the style sheet to specify a font just for Bangla / Bengali characters. This is certainly a workaround, and it does not render completely properly yet - but it is a start.

Here is what I did - pressed `ctrl+shift+p` to get access to the *console thingy* (Not quite sure what it is called).
{% figure caption:"The thing where I accessed the application style" %}
![The thing where I accessed the application style](https://farm8.staticflickr.com/7452/26728665931_255157ded4_z.jpg)

{% endfigure %}

Then, I added the following style:

{% highlight css %}
@font-face {
    font-family: 'bengali';
    src: local('Ekushey Durga');
    unicode-range: U+0980-09FF;
}

.markdown-preview.markdown-preview,
atom-text-editor::shadow .source.gfm {
    // use bengali at first for specified,
    //if not specified, use inconsolata
    font-family: bengali, 'inconsolata';
}

{% endhighlight %}

Of course, you will have to install `inconsolata` and `Ekushey Durga` font in advance to make it work. Enjoy!
