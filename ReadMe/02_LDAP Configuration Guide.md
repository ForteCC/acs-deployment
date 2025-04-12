## File Mounting Configuration
To connect Alfresco to LDAP, you must mount a custom properties file:

```yaml
volumes:
  - ./config/alfresco-global.properties:/usr/local/tomcat/shared/classes/alfresco-global.properties:ro
```

| Parameter | Description |
|-----------|-------------|
| `./config/alfresco-global.properties` | Source file path on host machine |
| `/usr/local/tomcat/shared/classes/alfresco-global.properties` | Target path in container |
| `:ro` | Read-only mount for security |

Apply changes with:
```bash
docker-compose up -d z #when its not running
docker-compose restart alfresco # when it is running
```
- create container if they dont exist.

## Core LDAP Authentication Settings

### Connection Credentials
```properties
ldap.authentication.java.naming.security.principal=CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
ldap.authentication.java.naming.security.credentials=PASSWORD
```

### Authentication Behavior
```properties
ldap.authentication.escapeCommasInBind=false  # Preserve commas in bind DN
ldap.authentication.escapeCommasInUid=false  # Preserve commas in usernames
defaultAdministratorUserNames=admin  # Always-admin users
synchronization.syncWhenMissingPeopleLogIn=true  # Sync new users on first login
```

## Detailed Synchronization Configuration

### User Query Parameters
```properties
# Base user query (active users only)
ldap.synchronization.personQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local))

# Differential query (changed users only)
ldap.synchronization.personDifferentialQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(!(modifyTimestamp<\={0})))
```

### Attribute Mapping
```properties
ldap.synchronization.userIdAttributeName=samAccountName  # AD username attribute
ldap.synchronization.userFirstNameAttributeName=givenName  # First name attribute
ldap.synchronization.userEmailAttributeName=userprincipalname  # Email attribute
```

### Search Base Configuration
```properties
ldap.synchronization.userSearchBase=OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
```

### Timestamp Handling
```properties
ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp  # Change tracking attribute
ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'  # AD timestamp format
```

### Performance Tuning
```properties
ldap.synchronization.queryBatchSize=1000  # Records per query
ldap.synchronization.attributeBatchSize=1000  # Attributes per batch
```

## Complete Configuration Reference

```properties
# Authentication Chain
authentication.chain=alfrescoNtlm1:alfrescoNtlm,ldap-ad1:ldap-ad

# LDAP Connection
ldap.authentication.active=true
ldap.authentication.allowGuestLogin=false
ldap.authentication.userNameFormat=CN=%s, OU=Users, OU=Tap Electric, DC=tapelectric, DC=local
ldap.authentication.java.naming.factory.initial=com.sun.jndi.ldap.LdapCtxFactory
ldap.authentication.java.naming.provider.url=ldap://10.20.102.10:389

# Synchronization Settings
ldap.synchronization.active=true
ldap.synchronization.java.naming.security.principal=CN=Mitesh Jalan, OU=Users, OU=Tap Electric, DC=tapelectric, DC=local
ldap.synchronization.java.naming.security.credentials=PASSWORD
synchronization.synchronizeChangesOnly=false
synchronization.allowDeletions=true

# Home Folder Configuration
ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider
ldap.synchronization.personType=user
ldap.synchronization.enableProgressEstimation=true
```

## Key Notes:
1. The `userAccountControl:1.2.840.113556.1.4.803:=512` filter ensures only active users are synced
2. Backslashes (`\`) escape special characters in properties files
3. The differential query uses `modifyTimestamp` to only sync changed records
4. Batch size parameters optimize performance for large directories




```
authentication.chain=alfrescoNtlm1:alfrescoNtlm,ldap-ad1:ldap-ad

ldap.authentication.active=true
ldap.authentication.allowGuestLogin=false
ldap.authentication.userNameFormat=CN=%s, OU=Users, OU=Tap Electric, DC=tapelectric, DC=local

ldap.authentication.java.naming.factory.initial=com.sun.jndi.ldap.LdapCtxFactory
ldap.authentication.java.naming.provider.url=ldap://10.20.102.10:389

ldap.authentication.java.naming.security.principal=CN=Mitesh Jalan, OU=Users, OU=Tap Electric, DC=tapelectric, DC=local
ldap.authentication.java.naming.security.credentials=ComplexHai@2692000

ldap.authentication.escapeCommasInBind=false
ldap.authentication.escapeCommasInUid=false
ldap.authentication.defaultAdministratorUserNames=admin

ldap.synchronization.active=true
ldap.synchronization.java.naming.security.principal=CN=Mitesh Jalan, OU=Users, OU=Tap Electric, DC=tapelectric, DC=local
ldap.synchronization.java.naming.security.credentials=ComplexHai@2692000
ldap.synchronization.queryBatchSize=1000
synchronization.synchronizeChangesOnly=false
synchronization.allowDeletions=true
synchronization.syncWhenMissingPeopleLogIn=true


ldap.synchronization.personQuery=(&(objectclass\=users)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users, OU=Tap Electric, DC=tapelectric, DC=local))
ldap.synchronization.personDifferentialQuery=(&(objectclass\=users)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users, OU=Tap Electric, DC=tapelectric, DC=local)(!(modifyTimestamp<\={0})))

ldap.synchronization.userSearchBase=OU=Users, OU=Tap Electric, DC=tapelectric, DC=local

ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp
ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'
ldap.synchronization.userIdAttributeName=samAccountName
ldap.synchronization.userFirstNameAttributeName=givenName
ldap.synchronization.userEmailAttributeName=userprincipalname
ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider
ldap.synchronization.personType=user
```


after removeing the sync got the error:
ERROR [repo.admin.ConfigurationChecker] [main] CONTENT INTEGRITY ERROR: System content not found in content store