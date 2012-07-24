---
layout: post
title: !binary |-
  R3JhaWxzLCBTcHJpbmcgU2VjdXJpdHkgJiBMZGFw
wordpress_id: 349
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zNDk=
date: 2011-01-06 15:25:32.000000000 +00:00
---
At work we're building a grails application which needs to authenticate users against our internal user directory using LDAP (Lightweight Directory something-or-other Protocol). Grails has two fantastic plugins to help here:

a) Spring security plugin
b) Spring security LDAP plugin

Now, getting the LDAP plugin to work has proved somewhat problematic, partially because of me rushing ahead, partially because documentation isn't quite as good as it could be. So to get the application to authenticate users with LDAP, there are two main ways of doing it.

1) Password comparison (where you have to do your own password encoding)
2) Bind authentication (where you pass on the username and password and let the LDAP directory authenticate)

for some daft reason, I started off down the Password comparison route, which was made more problematic when I found out that our internal LDAP directory uses an archaic form of password encryption. Once I'd stopped and re-read the documentation, a little light came on in my head and I started trying to get it to work with Bind authentication - then it doesn't matter how the password is encrypted, you're delegating that task.

The other part of the requirement is that the roles which will be retrieved following authentication will be from the application database (initially anyway) rather than the LDAP directory using a userDetailsService. So, to get everything working, the various Spring components need configuring manually, rather than relying on the plug in to do it.

So - how did I get it working against a real LDAP directory once the Spring Security &amp; LDAP plugins are installed?

Well, first, in the application configuration, set the ldap context:
<pre class="brush: plain;">grails.plugins.springsecurity.ldap.context.server = 'ldap://this is the ip address of my ldap directory:this is the port used'</pre>

Then, in the resources.groovy spring configuration file, set up the following:
<pre class="brush: groovy;">beans = {
     // this gives the pattern for authenticating the user, as the user doesn't want to enter the whole thing, 
     // just their unique id
     myLdapAuthenticator(org.springframework.security.ldap.authentication.BindAuthenticator, ref("contextSource")) {
         userDnPatterns = ['uid={0},ou=People,dc=people,dc=somewhereorother,dc=int']
     }

     // this overrides the default Authentication Provider with our authenticator and our user details service
     ldapAuthProvider(org.springframework.security.ldap.authentication.LdapAuthenticationProvider,
        ref("myLdapAuthenticator"),
        ref("userDetailsService")
     )

     // defining our user details service
     userDetailsService(com.companyname.service.UserDetailsService)   
}
</pre>
Now, when the application is started, spring security knows it needs to use LDAP to do it's business and once it's authenticated, it needs to use our user details service to return the list of roles. Hurrah!

PS - nearly forgot - to use the userDetailsService for retrieving the roles, it has to implement the org.springframework.security.ldap.userdetails.LdapAuthoritiesPopulator interface, returning a collection of org.springframework.security.core.GrantedAuthority
