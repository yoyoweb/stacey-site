Assets      {#intro}
======

In addition to any images or videos, stacey will also recognise any asset types placed within a page’s folder and push them into their own [collections][].

For example, this page:
![An example folder listing](/images/asset-file-listing.png)

will create the following collections:

<pre>
<em>$pdf</em> => array(
  './content/about/pdf-file.pdf'
)

<em>$mp3</em> => array(
  './content/about/mp3-file-1.mp3',
  './content/about/mp3-file-2.mp3'
)

<em>$html</em> => array(
  './content/about/youtube-embed.html'
)

<em>$doc</em> => array(
  './content/about/word-document.doc'
)

<em>$jpg</em> => array(
  './content/about/01.jpg'
)
</pre>

Each of these can be looped over within your templates or partials in the same way as the _$images_ or _$video_ collections.

Asset Collections   {#asset-collections}
-----------------

You can also create specific, named collections of assets. Stacey will recognise any folders beginning with an underscore as asset collections. These collections can be referenced using the name of the folder prefixed with a _$_ character.

ie. this directory structure:
![An example file listing for asset collections](/images/asset-collection-list.png)

will create the following asset collections:

<pre>
<em>$_logos</em> => array(
  './content/about/_logos/logo1.gif',
  './content/about/_logos/logo2.gif'
)

<em>$_thumbnails</em> => array(
  './content/about/_thumbnails/thumb1.jpg', 
  './content/about/_thumbnails/thumb2.jpg',
  './content/about/_thumbnails/thumb3.jpg',
  './content/about/_thumbnails/thumb4.jpg'
)
</pre>

Asset collection folders will not show up within any other collections (such as $siblings or $children).

Asset Types     {#asset-types}
-----------

Stacey knows how to construct a few asset types by default. Each type will be assigned its own set of variables which can then be accessed within the context of a loop.

### Images
(_.jpg_, _.jpeg_, _.gif_, _.png_)

**@name**
:   The name of the current image. This is constructed by converting the filename into sentence-text (ie. _1.my-image.jpg_ becomes _My image_).

**@file_name**
:   The filename of the current file. (ie. _1.my-image.jpg_)

**@url**
:  The relative path to this file from the current page. (ie. )

**@small**
:   The relative path to a file matching the name & filetype of the current file, with an \_sml suffix (if such a file exists). <i>ie. an image named _portrait.jpg_ would have an @small var of _portrait_sml.jpg_</i>

**@large**
:   The relative path to a file matching the name & filetype of the current file, with an \_lge suffix (if such a file exists). <i>ie. an image named _portrait.jpg_ would have an @large var of _portrait_lge.jpg_</i>
    
    

### Video  
(_.mov_, _.mp4_, _.m4v_, _.swf_)

**@name**
:   The name of the current video. This is constructed by converting the filename into sentence-text (ie. _1.my-movie.mov_ becomes _My movie_).

**@file_name**
:   The filename of the current file.

**@url**
:   The relative path to this file from the current page.

**@width**
:   The width of the current video (pulled from the name of the file – ie. <em>300</em>x150.mov).

**@height**
:   The height of the current video (pulled from the name of the file – ie. 300x<em>150</em>.mov).

### HTML
(_.html_, _.htm_)

**@name**
:   The name of the current video. This is constructed by converting the filename into sentence-text (ie. _1.my-youtube-video.html_ becomes _My youtube video_).

**@file_name**
:   The filename of the current file.

**@url**
:   The relative path to this file from the current page.

**@content**
:   The contents of the html file (as raw html).

### Any other assets
(_.*_)

**@name**
:   The name of the current video. This is constructed by converting the filename into sentence-text (ie. _1.my-resume.pdf_ becomes _My resume_).

**@file_name**
:   The filename of the current file.

**@url**
:   The relative path to this file from the current page.

[collections]: /documentation/variable-types/collections/