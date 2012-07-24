---
comments: false
date: 2009-05-27 10:22:40
layout: post
slug: catching-file-size-exceeded-when-using-tomahawk-file-upload-component
title: Catching 'file size exceeded' when using Tomahawk file upload component
wordpress_id: 230
---

When using T[omahawk's file upload component](http://myfaces.apache.org/tomahawk-project/tomahawk12/tagdoc/t_inputFileUpload.html) it isn't obvious how to catch what happens when you blow the file size limit. The file limit is set in the web.xml configuration for Tomahawk, i.e.



`  <filter>
<filter-name>extensionsFilter</filter-name>
<filter-class>org.apache.myfaces.webapp.filter.ExtensionsFilter</filter-class>
<init-param>
<description>
	Set the size limit for uploaded files. Format: 10 - 10
	bytes 10k - 10 KB 10m - 10 MB 1g - 1 GB
</description>
<param-name>uploadMaxFileSize</param-name>
<param-value>10m</param-value>
</init-param>
    .....
</filter>`



Here you can see the limit is set to 10 meg.

So by default, if you blow the limit, the component fails silently.. or does it?

Well, the component actually adds a couple of attributes to the request when refreshing the page (following the click of the upload button). The attributes are:
    
    <span>org.apache.myfaces.custom.fileupload.exception</span><span>
    org.apache.myfaces.custom.fileupload.maxSize</span>

by checking the request (during the page render) you can grab these attributes, if set, and display something meaningful to the user. You could have a little render tag at the top of the page to ensure the attributes are checked. Whilst this is a bit cronky, it is one of the jsf workarounds which does work.. in a fashion.

If they are present and you want to display the max size to the user, then apache commons FileUtils comes along to save the day


`[org.apache.commons.io.FileUtils.byteCountToDisplaySize](http://commons.apache.org/io/api-release/org/apache/commons/io/FileUtils.html#byteCountToDisplaySize(long))(new Long(maxSizeFromRequestAttribute));`
