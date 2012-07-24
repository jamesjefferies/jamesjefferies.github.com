---
layout: post
title: !binary |-
  TWlncmF0aW9uIGZyb20gTXlGYWNlcyAxLjEgdG8gMS4y
wordpress_id: 28
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9Mjg=
date: 2008-05-23 13:11:31.000000000 +00:00
---
Number of things need to be done:

1) Update dependencies for api and implementation jars
<blockquote>&lt;dependency&gt;
&lt;groupId&gt;org.apache.myfaces.core&lt;/groupId&gt;
&lt;artifactId&gt;myfaces-api&lt;/artifactId&gt;
&lt;version&gt;1.2.3&lt;/version&gt;
&lt;/dependency&gt;
&lt;dependency&gt;
&lt;groupId&gt;org.apache.myfaces.core&lt;/groupId&gt;
&lt;artifactId&gt;myfaces-impl&lt;/artifactId&gt;
&lt;version&gt;1.2.3&lt;/version&gt;
&lt;/dependency&gt;</blockquote>
Note: The api package replaces the standard javax.faces functionality. The iml is the actual implementation

2) Ensure that anything which depends on the javax.el (expression language) package doesn't pull it in to the maven build as we end up with the version embedded in myfaces *and* the version pulled in. This can be done by:
<blockquote>&lt;dependency&gt;
&lt;groupId&gt;org.jboss.jsfunit&lt;/groupId&gt;
&lt;artifactId&gt;jboss-jsfunit-core&lt;/artifactId&gt;
&lt;version&gt;1.0-beta-1&lt;/version&gt;
&lt;scope&gt;test&lt;/scope&gt;
&lt;exclusions&gt;
&lt;exclusion&gt;
&lt;artifactId&gt;el-api&lt;/artifactId&gt;
&lt;groupId&gt;javax.el&lt;/groupId&gt;
&lt;/exclusion&gt;
&lt;/exclusions&gt;
&lt;/dependency&gt;</blockquote>
and
<blockquote>&lt;dependency&gt;
&lt;groupId&gt;org.jboss.el&lt;/groupId&gt;
&lt;artifactId&gt;jboss-el&lt;/artifactId&gt;
&lt;version&gt;2.0.1.GA&lt;/version&gt;
&lt;exclusions&gt;
&lt;exclusion&gt;
&lt;artifactId&gt;el-api&lt;/artifactId&gt;
&lt;groupId&gt;javax.el&lt;/groupId&gt;
&lt;/exclusion&gt;
&lt;/exclusions&gt;
&lt;/dependency&gt;</blockquote>
Issues

Apparently JSF 1.2 and consequently MyFaces 1.2 move away from the old expression language to use some new unified version. This article describes it, but to be honest it all seems a bit of a faff.

This means that as our application stands, switching to 1.2 involves using some deprecated functionality. In BaseManagedBean the valuebinding functionality is now deprecated (in italics). It works, but at some point we'd want to switch it across, from ValueBinding to ValueExpression (easier said than done)

Object obj = FacesContext.getCurrentInstance().getApplication().<em>createValueBinding</em>("#{" +  bindingName + "}").<em>getValue</em>(FacesContext.getCurrentInstance());

<a title="JSF 1.2 release notes" href="http://java.sun.com/javaee/javaserverfaces/docs/ReleaseNotes.html#migrating" target="_blank">http://java.sun.com/javaee/javaserverfaces/docs/ReleaseNotes.html#migrating</a>

<a title="Migrating to Unified EL" href="http://java.sun.com/products/jsp/reference/techart/unifiedEL.html#Migrating_to_the_Unified_EL" target="_blank">http://java.sun.com/products/jsp/reference/techart/unifiedEL.html#Migrating_to_the_Unified_EL</a>
