---
layout: post
title: !binary |-
  U2V0dGluZyB1cCBzaW1wbGUgdGltZXIgam9icyB1c2luZyBRdWFydHo=
wordpress_id: 132
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD01
  NA==
date: 2009-02-18 11:07:21.000000000 +00:00
---
So traditionally, using cron on a server, calling a java method would be the default way of running some java code on a regular basis. Usually though you get tangled co-ordinating setting up the cron job, plus you have to write a specific method to be called which can be run from the command line. Before too long you're wiring up special persistence sessions to do the work.

There has to be a better way...

and there is! One option is to use the built in java.timer functions in the jdk. However, a better option might be to use Quartz.

<a title="Quartz" href="http://www.opensymphony.com/quartz/">Quartz</a> is a job scheduling system, encapuslated in a java library. You can do all sorts of funky stuff, including using cron like scheduling configuration. Everybody's happy.

To get it integrated though with your java app is made very easy if you are using <a href="http://www.springsource.org/">Spring</a>. We're using Spring 2.5 for this example, you can find out more here: <a href="http://static.springframework.org/spring/docs/2.5.x/reference/scheduling.html">Spring Scheduling</a>
<pre>	&lt;bean id="jobYouWantToRun" class="org.springframework.scheduling.quartz.MethodInvokingJobDetailFactoryBean"&gt;
  		&lt;property name="targetObject" ref="thisIsAReferenceToTheSpringBeanWithTheMethod" /&gt;
  		&lt;property name="targetMethod" value="thisIsTheMethodName" /&gt;
  		&lt;property name="concurrent" value="false" /&gt;
	&lt;/bean&gt;</pre>
So the config above sets up a job bean of type MethodInvoking blah - this takes a reference to a Spring Managed bean (one of your beans) and a method name, which is the method you want to run on a specific schedule.
<pre>	&lt;bean class="org.springframework.scheduling.quartz.SchedulerFactoryBean"&gt;
	    &lt;property name="triggers"&gt;
	        &lt;list&gt;
	            &lt;ref bean="cronTriggerForOurJob" /&gt;
	        &lt;/list&gt;
	    &lt;/property&gt;
	&lt;/bean&gt;</pre>
Here we set up the actual scheduler. We've only put one trigger in the list for example purposes. You can have simple triggers, for example, run every 100 seconds, or cron based triggers, which is what we've set up below.
<pre>	&lt;bean id="cronTriggerForOurJob" class="org.springframework.scheduling.quartz.CronTriggerBean"&gt;
	    &lt;property name="jobDetail" ref="jobYouWantToRun" /&gt;
	    &lt;property name="cronExpression" value="* 10 * ? * *" /&gt;</pre>
<pre>	&lt;/bean&gt;</pre>
The cron expression can be set up how you want, for <a href="http://quartz.sourceforge.net/javadoc/org/quartz/CronTrigger.html">more details</a>

So, when the Spring container is instantiated, it'll fire up quartz for you and before you know it, your method is being run on a regular basis.

Nothing needs to change in the Spring managed bean containing the method, it's all config in your Spring XML config. Hopefully in Spring 3.0 this can be done with annotations, making the link between the actual code in the class and the timer more explicit.
