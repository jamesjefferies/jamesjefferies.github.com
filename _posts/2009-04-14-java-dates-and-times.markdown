---
layout: post
title: !binary |-
  SmF2YSBkYXRlcyBhbmQgdGltZXMuLi4=
wordpress_id: 153
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MTg=
date: 2009-04-14 09:38:17.000000000 +00:00
---
.. have always been a bit of a crock. Lumpy and confusing. Apache common date utils have helped, but still you end up witing unintuitive code.

Many in the java community were hoping that JSR 310 was going to save the day, but it is looking more and more likely that it will not now make the cut for JDK 7. So, where does that leave us?

Hello <a href="http://joda-time.sourceforge.net/">Joda-Time</a>!

So, the drive behind JSR 310 was really incorporating Joda-Time in to the java specification. I've only just discovered Joda-Time and haven't used it in anger, but I really wish I'd found it sooner and will be looking to take it out for a spin at the earliest opportunity.

this, from the overview page gives you a tast of what Joda-Time gives you...
<pre>public boolean isAfterPayDay(DateTime datetime) {</pre>
<pre>  if (datetime.getMonthOfYear() == 2) {   // February is month 2!!</pre>
<pre>    return datetime.getDayOfMonth() &gt; 26;</pre>
<pre>  }</pre>
<pre>  return datetime.getDayOfMonth() &gt; 28;</pre>
<pre>}</pre>
<pre>public Days daysToNewYear(LocalDate fromDate) {</pre>
<pre>  LocalDate newYear = fromDate.plusYears(1).withDayOfYear(1);</pre>
<pre>  return Days.daysBetween(fromDate, newYear);</pre>
<pre>}</pre>
<pre></pre>
<pre>public boolean isRentalOverdue(DateTime datetimeRented) {</pre>
<pre>  Period rentalPeriod = new Period().withDays(2).withHours(12);</pre>
<pre>  return datetimeRented.plus(rentalPeriod).isBeforeNow();</pre>
<pre>}</pre>
<pre></pre>
<pre>public String getBirthMonthText(LocalDate dateOfBirth) {</pre>
<pre>  return dateOfBirth.monthOfYear().getAsText(Locale.ENGLISH);</pre>
<pre>}</pre>
