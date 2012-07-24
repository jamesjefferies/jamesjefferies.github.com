---
comments: false
date: 2009-03-11 11:49:03
layout: post
slug: migrating-from-hsqldb-to-mysql-part-1
title: Migrating from HSQLDB to MySQL - part 1
wordpress_id: 84
tags:
- databases
- java
- mysql
---

For this development project, we've been developing locally using in memory HSQLDB. The advantages of this are, easy set up out of the box (no database set up required), auto generation of schema from domain objects (thank you hibernate, using hbm2dll) and speed. A lightweight in memory db is good for us at this stage of the game.

Unfortunately though we need a proper database for when we go out in to the big world and as we can't use Oracle, we're going to make do with MySQL (just kidding here folks ;) )..

no, we really are using MySQL (see what I did there, I'm hilarious).

Of course, hibernate provides transparent mapping to which ever databases it supports out of the box.. nothing can, nor will it go wrong..

Hmm, see what I did their for comic effect? I can't help myself.

Fortunately, we're approaching 300 unit tests now, so switching to a real database should be a few configuration tweaks, prove the tests still run and off you go.

So, what issues did we hit:


#### MySQL doesn't 'support' sequences


You get used to sequences when developing with Oracle, hibernate lets you set a primary key as a sequence quite easily

    
    @Id
    @GeneratedValue(strategy = GenerationType.SEQUENCE)
    private Integer id;


of course, everything works nicely with HSQLDB, however switch to MySQL and it doesn't work. Fortunately from Hibernate 3.2.3 onwards, you can set up your own custom generator which will create a sequence table and use that instead, to emulate the behaviour of a sequence. A few magic annotations and off we go. What we do here is fire up the funky SequenceStyleGenerator (that's the new bit) telling it to use a table, which we can name if we want, plus I've named the columns and given the sequence a noddy name.

    
    @Id
    @GeneratedValue(generator="SuperDuperSequenceGenerator")
    @GenericGenerator
        name="SuperDuperSequenceGenerator",
        strategy="org.hibernate.id.enhanced.SequenceStyleGenerator",
        parameters={
    @Parameter(name="force_table_use", value="true"),
    @Parameter(name="value_column", value="value_column"),
    @Parameter(name="sequence_name", value="sequence_name")
    })



    
    private Integer id;




#### Don't make assumptions about column lengths


Set up a String property and HSQLDB will happily do that for you, doesn't care about length just works. I'm not advocating this is a good thing, but it is what it does. When you switch to using MySQL, this will default to a column with 255 characters. No problem with that default, but when you've happily chucked more than 255 characters in there, then MySQL will complain.

Simple solution, set the column size

    
    @Column(length=1000)


private String aThousandCharacterString;


#### Don't be a complete monkey spanner and use reserved words for domain objects or properties..


Of course, being experienced developers, we wouldn't get caught out with any of those puppies would we?

If we had, we'd recommend that people watch out for the following if nothing else.



	
  * Calling a domain object Trigger

	
  * Calling a domain object RoyRodgers

	
  * Calling a property lines


(by the way, one of those is just a joke)

If you *have* done the naughty, then all is not lost. You could refactor everything, or simply specificy an explicit table or column name.. i.e.

    
    @Column(name="LinesToRender")
    private Integer lines;


or

    
    @Entity
    @Table(name="DiversityTrigger")
    public class Trigger




#### Set the correct dialogue property in the hibernate properties



    
    hibernate.dialect=org.hibernate.dialect.MySQLInnoDBDialect
