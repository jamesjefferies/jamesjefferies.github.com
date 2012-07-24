---
comments: false
date: 2009-04-14 11:41:31
layout: post
slug: gotcha-with-auto-ddl-generation-and-hibernate
title: Gotcha with auto DDL generation and hibernate
wordpress_id: 155
---

During project development, we're auto creating our database when the application initiates. This is superuseful initially, especially when the database is based on the domain objects rather than the other way around. Since switching to MySQL and a 'real' database, rather than one in memory, there are a few gotchas. The one which caught me out this morning, for a few hours, involved adding and removing foreign keys automagically... it doesn't really work!

this is useful by the way for [hibernate config](http://www.hibernate.org/hib_docs/reference/en/html/configuration-optional.html) as is [this](http://www.jroller.com/eyallupu/entry/hibernate_s_hbm2ddl_tool)

anyway, we were set - `hibernate.hbm2ddl.auto=create`

when actually, we should have used create-drop.

create will empty the database, whereas create-drop will properly drop it...

for completeness, here is the configuration for a entity manager, with the generate DDL parameter switching the ddl generation on and off, and the hibernate.hbm2ddl.auto parameter determining whether you do a create each time or an update or whatever.

    
    <bean id="entityManagerFactory" class="org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean">
            <property name="loadTimeWeaver">
                <bean class="org.springframework.instrument.classloading.InstrumentationLoadTimeWeaver" />
            </property>
            <property name="persistenceUnitName" value="projectNamePU" />
            <property name="jpaPropertyMap">
                <map>
                    <entry key="hibernate.search.default.directory_provider" value="org.hibernate.search.store.RAMDirectoryProvider"  />   
                    <entry key="hibernate.cache.provider_class" value="net.sf.ehcache.hibernate.SingletonEhCacheProvider" />
                    <entry key="hibernate.cache.provider_configuration" value="classpath:ehCache.xml" />
                    <entry key="hibernate.cache.use_second_level_cache" value="true" />
                    <entry key="hibernate.generate_statistics" value="true" />
                    <entry key="hibernate.cache.use_structured_entries" value="true" />
                    <entry key="hibernate.jdbc.batch_size" value="0" />
                <entry key="hibernate.default_batch_fetch_size" value="20"/>
                <span style="color: #ff0000"><entry key="hibernate.hbm2ddl.auto" value="${hibernate.hbm2ddl.auto}" /></span>
                </map>
            </property>
    
            <property name="dataSource" ref="dataSource"/>
            <property name="jpaVendorAdapter">
               <bean class="org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter">
                    <property name="database" value="${hibernate.database}" />
                    <property name="showSql" value="${hibernate.show_sql}" />
                    <span style="color: #ff0000"><property name="generateDdl" value="${hibernate.generate_ddl}" /></span>
                    <property name="databasePlatform" value="${hibernate.dialect}" />
                </bean>          
            </property>
        </bean>
