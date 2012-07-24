---
comments: false
date: 2009-04-14 09:38:17
layout: post
slug: java-dates-and-times
title: Java dates and times...
wordpress_id: 153
tags:
- java
---

.. have always been a bit of a crock. Lumpy and confusing. Apache common date utils have helped, but still you end up witing unintuitive code.

Many in the java community were hoping that JSR 310 was going to save the day, but it is looking more and more likely that it will not now make the cut for JDK 7. So, where does that leave us?

Hello [Joda-Time](http://joda-time.sourceforge.net/)!

So, the drive behind JSR 310 was really incorporating Joda-Time in to the java specification. I've only just discovered Joda-Time and haven't used it in anger, but I really wish I'd found it sooner and will be looking to take it out for a spin at the earliest opportunity.

this, from the overview page gives you a tast of what Joda-Time gives you...

``` java    
    public boolean isAfterPayDay(DateTime datetime) {
    
      if (datetime.getMonthOfYear() == 2) {   // February is month 2!!
        return datetime.getDayOfMonth() > 26;
      }
      return datetime.getDayOfMonth() > 28;
    }
    
    public Days daysToNewYear(LocalDate fromDate) {
      LocalDate newYear = fromDate.plusYears(1).withDayOfYear(1);
      return Days.daysBetween(fromDate, newYear);
    }
    
    public boolean isRentalOverdue(DateTime datetimeRented) {
      Period rentalPeriod = new Period().withDays(2).withHours(12);
      return datetimeRented.plus(rentalPeriod).isBeforeNow();
    }
    
    public String getBirthMonthText(LocalDate dateOfBirth) {
      return dateOfBirth.monthOfYear().getAsText(Locale.ENGLISH);
    }
```
