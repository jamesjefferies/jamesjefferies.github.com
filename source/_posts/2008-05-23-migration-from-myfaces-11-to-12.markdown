---
comments: false
date: 2008-05-23 13:11:31
layout: post
slug: migration-from-myfaces-11-to-12
title: Migration from MyFaces 1.1 to 1.2
wordpress_id: 28
---

Number of things need to be done:

1) Update dependencies for api and implementation jars


> <dependency>
<groupId>org.apache.myfaces.core</groupId>
<artifactId>myfaces-api</artifactId>
<version>1.2.3</version>
</dependency>
<dependency>
<groupId>org.apache.myfaces.core</groupId>
<artifactId>myfaces-impl</artifactId>
<version>1.2.3</version>
</dependency>


Note: The api package replaces the standard javax.faces functionality. The iml is the actual implementation

2) Ensure that anything which depends on the javax.el (expression language) package doesn't pull it in to the maven build as we end up with the version embedded in myfaces *and* the version pulled in. This can be done by:


> <dependency>
<groupId>org.jboss.jsfunit</groupId>
<artifactId>jboss-jsfunit-core</artifactId>
<version>1.0-beta-1</version>
<scope>test</scope>
<exclusions>
<exclusion>
<artifactId>el-api</artifactId>
<groupId>javax.el</groupId>
</exclusion>
</exclusions>
</dependency>


and


> <dependency>
<groupId>org.jboss.el</groupId>
<artifactId>jboss-el</artifactId>
<version>2.0.1.GA</version>
<exclusions>
<exclusion>
<artifactId>el-api</artifactId>
<groupId>javax.el</groupId>
</exclusion>
</exclusions>
</dependency>


Issues

Apparently JSF 1.2 and consequently MyFaces 1.2 move away from the old expression language to use some new unified version. This article describes it, but to be honest it all seems a bit of a faff.

This means that as our application stands, switching to 1.2 involves using some deprecated functionality. In BaseManagedBean the valuebinding functionality is now deprecated (in italics). It works, but at some point we'd want to switch it across, from ValueBinding to ValueExpression (easier said than done)

Object obj = FacesContext.getCurrentInstance().getApplication()._createValueBinding_("#{" +  bindingName + "}")._getValue_(FacesContext.getCurrentInstance());

[http://java.sun.com/javaee/javaserverfaces/docs/ReleaseNotes.html#migrating](http://java.sun.com/javaee/javaserverfaces/docs/ReleaseNotes.html#migrating)

[http://java.sun.com/products/jsp/reference/techart/unifiedEL.html#Migrating_to_the_Unified_EL](http://java.sun.com/products/jsp/reference/techart/unifiedEL.html#Migrating_to_the_Unified_EL)
