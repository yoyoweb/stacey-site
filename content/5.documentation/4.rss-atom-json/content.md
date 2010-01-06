RSS/Atom/JSON     {#intro}
=============

Stacey doesn’t make too many assumptions about which format your templates are written in. It uses the extension of the template file to work out what type of content it should be serving. By default stacey will recognise and serve the correct content-types for _.html_, _.json_, _.xml_, _.atom_, _.rss_, _.rdf_ & _.txt_ files.

In fact, this is how the default RSS feed is built. The _/content/feed_ directory is just a normal stacey page, the only difference is that it uses .atom rather than .html template files.

So, if you wanted to switch out Atom for the RSS2 format, your _/templates/feed.atom_ template could be renamed to _feed.rss_ and changed to look something like this:

<pre>
&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;rss version=&quot;2.0&quot;&gt;
  &lt;channel&gt;
    &lt;title&gt;<em>@name</em>&apos;s <em>@feed_name</em>&lt;/title&gt;
    &lt;link&gt;http://<em>@base_url</em>/<em>@permalink</em>/&lt;/link&gt;
    &lt;description&gt;<em>@description</em>&lt;/description&gt;

  <em>&#58;feed_loop</em>

  &lt;/channel&gt;
&lt;/rss&gt;
</pre>

Additionally, stacey creates file extension shortcuts for all the file types listed above. This means rather than having to point to http://yourdomain.com<em>/feed/</em>, you could shortcut this to http://yourdomain.com<em>/feed.atom</em>.