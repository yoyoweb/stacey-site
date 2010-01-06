Overview                   {#intro}
========

Stacey was devised as a simple framework for extending static html websites. It is essentially a regular-expression-based templating system which uses a file system datastore rather than a traditional relational database.

The stacey project is based around two simple ideals:

1.  to remove the requirement of html knowledge to manage site content
2.  to remove the requirement of php knowledge to edit html templates.

These two ideals map directly to the <em>/content</em> and <em>/template</em> folders respectively.

This is achieved through three core components, a text file parser, a template parser & the file system datastore. These fit together to make an extremely flexible and powerful content management system.

Because stacey uses the file system to store and manage data, it means you are able to build & deploy sites extremely quickly. Additionally, as php is so common, stacey-based sites can be deployed very cost-effectively and to pretty much any standard hosting package.


### It Caches                 {#caching}

Because reading a file system can become slow on larger sites, stacey uses a combination of file-based caching & e-tag headers to ensure pages are always loaded as fast as possible. The caching system doesn’t use an arbitrary time-based cache expiry, instead it relies on a system which only rebuilds the cache when something has changed.


### It’s small    {#lightweight}

The entire codebase is around 600 lines of code, so it shouldn’t be too hard to read through, get an idea of how it works & extend for your own purposes.

The project is maintained over at _<http://github.com/kolber/stacey>_, so pick through the code, suggest improvements, or fork it & fix things yourself.