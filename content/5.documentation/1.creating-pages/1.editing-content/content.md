Content Editing           {#content-editing}
===============

Within the _/content_ directory, there is a file named _\_shared.txt_.

If you open it up with a text editor, you should see:
<pre>
name: <em>Name</em>

profession: <em>Graphic Designer</em>

email: <em>hi@yourdomain.com</em>
</pre>

Replace the highlighted data with your own details.

### Text file encoding    {#text-file-encoding}

All of your .txt files should be encoded using UTF-8. In addition to ensuring no strange characters are inserted which could break stacey’s rendering engine, this will also allow you to use special characters such as _&ouml;_, _&mdash;_ or double-byte characters such as _照_ or _ラ_.

Any decent text editor will give you the options to edit and save your text files as UTF-8, so google should be able to provide answers on how to do this with your editor of choice.

You can read more about [text files][] & [UTF-8 encoding][] on Wikipedia.



### Editing content       {#editing-content}
Each folder which is to be displayed as a page should have a _.txt_ file inside it (even if this text file is empty). The name of the .txt file should match up with a file in the _/templates_ folder, as this is how you select which template to use for each page.
![Screenshot of /content folder with 'project.txt' selected](/images/projects-contents-file.png)
![Screenshot of /templates folder with 'project.html' selected](/images/template-selected.png)

The content files all follow a standard format; each _key_ is followed by a _:_, a _value_ and two newline characters. 
<pre>
<em>key</em>: <em>value 
 </em>
</pre>

The keys match up with variable markers in the template files which get replaced with the contents of the _value_. You can create as many of your own keys as you need.

A key may only contain the following characters:  
~~~~~~~~~~~~~~~~~
abcdefghijklmnopqrstuvwxyz
0123456789
_
~~~~~~~~~~~~~~~~~

Essentially, lowercase latin alphanumeric characters and underscores.  
Or, for the more technically inclined, anything which can be matched by the following regular expression: _`/[a-z0-9_]+?:/`_

A standard content file looks something like this:
<pre>
title: The Test Project 1

date: 2009, Jun—

content: 
Lorem ipsum dolor...

</pre>

Each value should have a clear line following it.

<pre>
<em>title: 	The Test Project 1
</em>
date: ...
</pre>

If you want one of the values to be empty, leave a space after the colon.

<pre>
title:<em> </em>

date: ...
</pre>

### Advanced editing      {#advanced-editing}

#### Paragraphs           {#paragraphs}

If you have text that spans multiple paragraphs, start the text on a new line following the colon, then start each following paragraph on another new line.
<pre>
content:
<em>paragraph 1
paragraph 2</em>
</pre>

Or if you have single line that you want wrapped in a paragraph, start it on a new line after the colon.

<pre>
content:
<em>paragraph 1</em>
</pre>

#### Bulleted lists          {#bulleted-lists}

To define the text as a bulleted list, start the text on a new line following the colon, then start each bullet point on another new line, preceded by a hyphen (-).
<pre>
content:
<em>- value 1
- value 2</em>
</pre>
#### Email addresses and urls {#emails-and-urls}

Anything that looks like a url (ie. <em>http://www.staceyapp.com</em>) will be automatically turned into a link. The same goes for email addresses (ie. <em>info@staceyapp.com</em>).

#### Inline html            {#inline-html}

If you want to get a little more advanced, you can use html within your values, although you will need to keep the html to one line (as stacey uses newlines to separate keys and values).

<pre>
content: <em>&lt;strong&gt;</em>paragraph 1<em>&lt;/strong&gt;</em>
</pre>

## How variables are created:  {#how-variables-are-created}
<ol>
	<li>Browser hits <em>http://yourdomain.com/about/</em>.</li>
	<li>
		<p>Stacey reads the appropriate content file <em>/content/3.about/content.txt</em>.</p>
<pre>
title: About Title

content: Lorem ipsum.
</pre>
	</li>
	<li>Two variables are extracted from the keys & values from within the .txt file: <em>@title</em> & <em>@content</em>. These will be available for use within the templates.</li>
	<li>Stacey finds the matching template file, in this case, <em>/templates/content.html</em></li>
	<li>
		<p>Stacey replaces the variables in the template and outputs the final html.</p>
		<p>So this template code:</p>
<pre>
&lt;div id=&quot;main&quot;&gt;
&lt;h1&gt;<em>@title</em>&lt;/h1&gt;
&lt;p&gt;<em>@content</em>&lt;/p&gt;
&lt;/div&gt;
</pre>
	<p>becomes this html:</p>
<pre>
&lt;div id=&quot;main&quot;&gt;
&lt;h1&gt;<em>About Title</em>&lt;/h1&gt;
&lt;p&gt;<em>Lorem ipsum.</em>&lt;/p&gt;
&lt;/div&gt;
</pre>
	</li>
</ol>

[text files]: http://en.wikipedia.org/wiki/Text_file
[UTF-8 encoding]: http://en.wikipedia.org/wiki/UTF-8