---
comments: false
date: 2009-11-17 18:54:23
layout: post
slug: jsf-2-highlights
title: JSF 2 highlights…
wordpress_id: 254
tags:
- linkedin
---

As a relatively experienced JSF 1.2 user I have high hopes for the next generation of the JSF framework. Consequently I gave up my afternoon to have my JSF world blown away.. or something.

So, here are some highlights about what's new in JSF 2



	
  * Bye bye XML -  get rid of a lot of the silly XML configuration and replace it with annotations. JSF 1.x is weighed down with it's verbose XML config and half-baked dependency injection, JSF 2 is much better

	
  * Facelets is now the default renderer - and about time, using XHTML and facelets has always fitted better with JSF than compiled JSP.

	
  * Composite components - the component model has been souped up to be far more useable, especially with simple ways to make composites.

	
  * Standard AJAX tags - seem to work great but are obtrusive :(

	
  * Partial State saving - no more performance issues with saving the state all the time, sensible deltas are now stored, phew!

	
  * PreRenderViewEvent and PostAddToViewEvent - nice extendable ways to do on page load, on validation and all that stuff.

	
  * Navigation short cuts - instead of going crazy with navigation xml, sensible defaults are now provided. return "catalog" would default to rendering /catalog.xhtml as you would hope

	
  * Conditional navigation - still xml, but much cleverer now for allowing navigation logic in config rather than in the bean.

	
  * JSR 299 beans - full on dependency injection including flash scope and all sorts of other goodies. This looks great but a bit different from how we've done it with Spring in the past.

	
  * Proper bean validation - annotate the domain objects and bean validation can take place in one place on the server side, all wired up to the JSF lifecycle. Looks like a lifesaver. JSR 303 @NotNull @Email - you got to love that!

	
  * Validation groups - can group sets of validations.. nice.

	
  * Pluggable error dispatcher - holy moly, this is almost the holy grail - throw errors in a sensible way with extensibility made easy.

	
  * Still uses web.xml though :/


So in summary, there is lots of good stuff included in JSF 2.0, the problem is that it hasn't been released yet, either as MyFaces or a RI implementation in a version fit for production. I want to give JSF 2.0 a go, but by that time I may have converted to wicket, or grails, or lift or loom or anything else which does most of this stuff just as well or better..

oh and no mention of portlets!
