---
layout: post
title: !binary |-
  R290Y2hhIHdpdGggYXV0byBEREwgZ2VuZXJhdGlvbiBhbmQgaGliZXJuYXRl
wordpress_id: 155
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MjA=
date: 2009-04-14 11:41:31.000000000 +00:00
---
During project development, we're auto creating our database when the application initiates. This is superuseful initially, especially when the database is based on the domain objects rather than the other way around. Since switching to MySQL and a 'real' database, rather than one in memory, there are a few gotchas. The one which caught me out this morning, for a few hours, involved adding and removing foreign keys automagically... it doesn't really work!

this is useful by the way for <a href="http://www.hibernate.org/hib_docs/reference/en/html/configuration-optional.html">hibernate config</a> as is <a href="http://www.jroller.com/eyallupu/entry/hibernate_s_hbm2ddl_tool">this</a>

anyway, we were set - <code>hibernate.hbm2ddl.auto=create</code>

when actually, we should have used create-drop.

create will empty the database, whereas create-drop will properly drop it...

for completeness, here is the configuration for a entity manager, with the generate DDL parameter switching the ddl generation on and off, and the hibernate.hbm2ddl.auto parameter determining whether you do a create each time or an update or whatever.
<pre>&lt;bean id="entityManagerFactory" class="org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean"&gt;
        &lt;property name="loadTimeWeaver"&gt;
            &lt;bean class="org.springframework.instrument.classloading.InstrumentationLoadTimeWeaver" /&gt;
        &lt;/property&gt;
        &lt;property name="persistenceUnitName" value="projectNamePU" /&gt;
        &lt;property name="jpaPropertyMap"&gt;
            &lt;map&gt;
                &lt;entry key="hibernate.search.default.directory_provider" value="org.hibernate.search.store.RAMDirectoryProvider"  /&gt;   
                &lt;entry key="hibernate.cache.provider_class" value="net.sf.ehcache.hibernate.SingletonEhCacheProvider" /&gt;
                &lt;entry key="hibernate.cache.provider_configuration" value="classpath:ehCache.xml" /&gt;
                &lt;entry key="hibernate.cache.use_second_level_cache" value="true" /&gt;
                &lt;entry key="hibernate.generate_statistics" value="true" /&gt;
                &lt;entry key="hibernate.cache.use_structured_entries" value="true" /&gt;
                &lt;entry key="hibernate.jdbc.batch_size" value="0" /&gt;
            &lt;entry key="hibernate.default_batch_fetch_size" value="20"/&gt;
            <span style="color: #ff0000">&lt;entry key="hibernate.hbm2ddl.auto" value="${hibernate.hbm2ddl.auto}" /&gt;</span>
            &lt;/map&gt;
        &lt;/property&gt;

        &lt;property name="dataSource" ref="dataSource"/&gt;
        &lt;property name="jpaVendorAdapter"&gt;
           &lt;bean class="org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter"&gt;
                &lt;property name="database" value="${hibernate.database}" /&gt;
                &lt;property name="showSql" value="${hibernate.show_sql}" /&gt;
                <span style="color: #ff0000">&lt;property name="generateDdl" value="${hibernate.generate_ddl}" /&gt;</span>
                &lt;property name="databasePlatform" value="${hibernate.dialect}" /&gt;
            &lt;/bean&gt;          
        &lt;/property&gt;
    &lt;/bean&gt;</pre>
