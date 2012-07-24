---
layout: post
title: !binary |-
  TWF2ZW4gcmVsb2FkZWQgKGZyb20gZGV2b3h4KQ==
wordpress_id: 265
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNjU=
date: 2009-12-06 20:59:03.000000000 +00:00
---
Jason Van Zyl was the speaker for this session, the creator of Maven - he know works for sonatype and will shortly be moving on from Maven to other things. The points below are highlight points from his talk at devoxx.

It was acknowledged that many things were wrong with maven 2.0 and version 3.0 is a chance to put those things right - adding extras like support for m2eclipse and osgi.

Maven has moved from where it originally was set up. The main driver for changes are 'desire lines' - difference between how things were intended and how people used things. Responding to invitations for improvement. How people check out whole source trees, mis use of the release plugin. Responding to under utilization of what exists.

Maven 3 should be backwards compatible with maven 2, so we should be good to go with maven 3 - performance benefits?

Pluggable modelreader for project builder (which has been refactored). mixins for poms, composition for poms. Keep hold of non-mutated model and track contributions to pom. Might have a 'spring mixin' or 'tomcat depoy mixin' or whatever, these can be stored in the reposoitory.

More extension points on maven 3, decorate the lifecycle. DSLs can do all this, in groovy, ruby, scala, python.

The queryable lifecycle. Can query the execution plan before it happens (which is what M2Eclipse now does). Big performance increase now in eclipse.

Incremental build support. in M2 loads of stuff has been delegated to eclipse.

Lifecycle extension points Tycho - maven plugins delegates stuff to OSGI/Eclipse stuff.

Aggregator problems with maven 2, in 3, the post build works properly so report aggregation should work correctly.

Tycho is the complete replacement for PDE headless build, buckminster and everything else that attmeptes to builf OSGI.

Maven 3 used in hudson, M2Eclipse and netbeans already...

Maven shell looks brilliant, a make-like reactor, the shell caches the poms and all sorts of stuff.

Better error and inntegrity reporting. Lots of problems have a link to a wiki entry in confluence. Catalog to read about it. In the shell or m2eclipse, that data can be pulled in. Don't allow builds where versions come from profiles which have to be activated manually.

Plugin manager, switched over to OSGI runtime, conceierge, guice and peaberry. Creating isolated classloader and stuff, but decided to switch to OSGI instead. Hudson will be switched across to OSGI as well. Plexus going in maven 3.1, replaced by Guice.

Plugin extension points, will be in 3.1 - rip off of Eclipse plugin.

Replace HTTP stuff with jetty client. SSL, PGP SUPPORT, multiple threaded downloads and all that.

End of january for 3.0 release.

Extensible reporting. Logic is now in maven site plugin rather than contined in the core. Static maven sites will probably disappear.

Guice and peaberry. Plexus has been going as long as spring, was ahead, but now.... not kept up. Needed more speed and injection listening - use guice with in effect a wrapper so all the plexus stuff still works as was. Use JSR330 in the future.
