Variables     {#intro}
=========

Within the templates files, apart from our standard html, we also have access to any variables defined within the .txt file that corresponds to the current page. These can be accessed by using an _@_ symbol followed by the _key_.

<i>ie. <em>@title</em></i>

In addition, any variables defined in _/content/_shared.txt_ are available within all template files.

Stacey-created variables      {#stacey-created-variables}
------------------------

These are created for each page within the site.

**@root_path**
:   Will output a relative path from the current page to the root of the site.
    <i>ie. in _/projects/project-name/_ @root\_path will contain _../../_.</i>
    
**@thumb**
:   Outputs the relative url to the thumbnail for this page (if one exists).

**@url**
:   Outputs the relative path to this page from the page currently being viewed (ie. _../../projects/project-1_).

**@permalink**
:   Outputs the absolute url path of the current page (ie. _projects/project-1_).

**@slug**
:   Outputs the slug of the current page (ie. _project-1_).

**@is_current_page**
:   Returns true if _@permalink_ matches the server’s request uri.

**@page_name**
:   Outputs the name of the current page.  
    This is constructed by converting the page’s slug into title-case text  
    (ie. _test-project-1_ becomes _Test Project 1_).

**@siblings_count**
:   The number of pages sitting at the same level as this page (ie. _12_).

**@index**
:   The number of the current page, relative to the other pages sitting at the same level (ie. _5_).

**@current_year**
:   Will output the current year.

**@domain_name**
:   Will output the domain name of the current site (ie. _staceyapp.com_).

**@base_url**
:   Will output the domain name & folder path stacey is running from  
    (ie. _staceyapp.com/stacey_).

**@site_updated**
:   Will output the date the site was last edited in the [RFC 3339][] format  
    (ie. _2009-12-12T17&#58;34&#58;23+11&#58;00_).

**@updated**
:   Will output the date the current page was last edited in the [RFC 3339][] format (ie. _2009-12-12T17&#58;34&#58;23+11&#58;00_).

**@stacey_version**
:   Will output the version of stacey you are running (ie. _2.0_).

[RFC 3339]: http://tools.ietf.org/html/rfc3339