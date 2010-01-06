Templating Language       {#intro}
===================
Stacey pre-parses each template as plain text before it is rendered out as html. As the templating system runs off regular expressions, there is no need to explicitly wrap the language constructs in `<?php ?>` tags.

Language Constructs       {#language-contructs}
-------------------
Within stacey templates, you have access to three language constructs: _`get`_ statements, _`foreach`_ loops & boolean _`if`_ statements.

<dl class="thin">
	<dt><strong>foreach</strong></dt>
	<dd>
<pre>
<em>&#102;oreach $collection do</em>
  # do stuff
<em>endforeach</em>
</pre>
  </dd>
</dl>
<dl class="thin">
	<dt><strong>if</strong></dt>
	<dd>
<pre>
<em>i&#102; @variable do</em>
  # do stuff
<em>endif</em>
</pre>
	</dd>
</dl>
<dl class="thin">
	<dt><strong>if not</strong></dt>
	<dd>
<pre>
<em>i&#102; !@variable do</em>
  # do stuff
<em>endif</em>
</pre>
	</dd>
</dl>

### Variable Context      {#variable-context}

Once you are inside a foreach loop, the variable context changes to the current object being referenced by the loop. So in the above example, we are accessing the _@url_ & _@page_name_ variables for each page being looped over.

If you want to shift to the context of a specific page, you can add a _`get`_ call to the top of your partial or template.

<pre>
<em>get "/projects"</em>
</pre>

This will change the context from the current page being viewed to the _/projects_ page. This means _$children_ will be filled with the children of the /projects page, _@page_name_ will equal 'Projects', etc.

So, if you wanted to only list children of the /projects folder which do not contain children of their own, you could construct the following partial:
  
<pre>
get "<em>/projects</em>"

&#102;oreach <em>$children</em> do
  i&#102; !<em>$children</em> do
    &lt;p&gt;&lt;a href=&quot;<em>@url</em>&quot;&gt;<em>@page_name</em>&lt;/a&gt;&lt;/p&gt;
  endif
endforeach
</pre>

### Nesting foreach Loops     {#foreach-nesting}

To give you the ability to pass through multiple levels of objects, foreach loops can also be nested within themselves (although using [recursive partials][] would be a more elegant solution).

<pre>
&lt;ol id=&quot;navigation&quot;&gt;
  <em>&#102;oreach $root do</em>
    &lt;li&gt;&lt;a href=&quot;@url&quot;&gt;@page_name&lt;/a&gt;
      <em>i&#102; $children do</em>
        &lt;ol&gt;
          <em>&#102;oreach $children do</em>
            &lt;li&gt;&lt;a href=&quot;@url&quot;&gt;@page_name&lt;/a&gt;
          <em>endforeach</em>
        &lt;/ol&gt;
      <em>endif</em>
    &lt;/li&gt;
  <em>endforeach</em>
&lt;/ol&gt;
</pre>

[recursive partials]: /documentation/variable-types/partials/#recursive-partials