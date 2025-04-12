Enable Detailed logging:
./local/tomcat/webapps/alfresco/WEB-INF/classes/log4j2.properties
make changes here.


---


/usr/local/tomcat/webapps/alfresco/WEB-INF/classes/log4j2.properties
 
 Alfresco LDAP Sync
logger.alfresco-ldap-sync.name=org.alfresco.repo.security.sync.ldap
logger.alfresco-ldap-sync.level=DEBUG

# Spring LDAP (used by Alfresco)
logger.spring-ldap.name=org.springframework.ldap
logger.spring-ldap.level=DEBUG

# JNDI (LDAP connection handling)
logger.jndi.name=javax.naming
logger.jndi.level=TRACE

# LDAP authentication
logger.alfresco-ldap-auth.name=org.alfresco.repo.security.authentication.ldap
logger.alfresco-ldap-auth.level=DEBUG

# Enable raw LDAP traffic logging (for deep debugging)
logger.ldap-ber.name=com.sun.jndi.ldap
logger.ldap-ber.level=TRACE
