---
layout: post
title: !binary |-
  Q2F0Y2hpbmcgJiMwMzk7ZmlsZSBzaXplIGV4Y2VlZGVkJiMwMzk7IHdoZW4g
  dXNpbmcgVG9tYWhhd2sgZmlsZSB1cGxvYWQgY29tcG9uZW50
wordpress_id: 230
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yMzA=
date: 2009-05-27 10:22:40.000000000 +00:00
---
<p>When using T<a href="http://myfaces.apache.org/tomahawk-project/tomahawk12/tagdoc/t_inputFileUpload.html">omahawk's file upload component</a> it isn't obvious how to catch what happens when you blow the file size limit. The file limit is set in the web.xml configuration for Tomahawk, i.e.</p>

<code>  &lt;filter&gt;
&lt;filter-name&gt;extensionsFilter&lt;/filter-name&gt;
&lt;filter-class&gt;org.apache.myfaces.webapp.filter.ExtensionsFilter&lt;/filter-class&gt;
&lt;init-param&gt;
&lt;description&gt;
	Set the size limit for uploaded files. Format: 10 - 10
	bytes 10k - 10 KB 10m - 10 MB 1g - 1 GB
&lt;/description&gt;
&lt;param-name&gt;uploadMaxFileSize&lt;/param-name&gt;
&lt;param-value&gt;10m&lt;/param-value&gt;
&lt;/init-param&gt;
    .....
&lt;/filter&gt;</code>

<p>Here you can see the limit is set to 10 meg.</p> <p>So by default, if you blow the limit, the component fails silently.. or does it?</p> <p>Well, the component actually adds a couple of attributes to the request when refreshing the page (following the click of the upload button). The attributes are:</p> <pre><span>org.apache.myfaces.custom.fileupload.exception</span><span>
org.apache.myfaces.custom.fileupload.maxSize</span></pre><p>by checking the request (during the page render) you can grab these attributes, if set, and display something meaningful to the user. You could have a little render tag at the top of the page to ensure the attributes are checked. Whilst this is a bit cronky, it is one of the jsf workarounds which does work.. in a fashion.</p> <p>If they are present and you want to display the max size to the user, then apache commons FileUtils comes along to save the day</p>
<code><a href="http://commons.apache.org/io/api-release/org/apache/commons/io/FileUtils.html#byteCountToDisplaySize(long)">org.apache.commons.io.FileUtils.byteCountToDisplaySize</a>(new Long(maxSizeFromRequestAttribute));</code>
