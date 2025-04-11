- To connect to ldap go to the properties file at:
  /usr/local/tomcat/shared/classes/
- Now add following code:
```bash
authentication.chain=alfrescoNtlm1:alfrescoNtlm,ldap-ad1:ldap-ad  
ldap.authentication.active=true  
ldap.authentication.allowGuestLogin=true  
ldap.authentication.userNameFormat=%[s@xxx.x](mailto:s@pucsl.lk)x  
ldap.authentication.java.naming.factory.initial=com.sun.jndi.ldap.LdapCtxFactory  
ldap.authentication.java.naming.provider.url=ldap://[xxx](mailto:s@pucsl.lk)[.](http://pucsl.lk:389/)[xx](mailto:s@pucsl.lk)[:389](http://pucsl.lk:389/)  
ldap.authentication.java.naming.security.authentication=simple  
ldap.authentication.escapeCommasInBind=false  
ldap.authentication.escapeCommasInUid=false  
ldap.authentication.defaultAdministratorUserNames=Administrator

ldap.synchronization.active=true  
ldap.synchronization.java.naming.security.principal=[administrator@](mailto:administrator@pucsl.lk)[xxx](mailto:s@pucsl.lk)[.](mailto:administrator@pucsl.lk)[xx](mailto:s@pucsl.lk)  
ldap.synchronization.java.naming.security.credentials=secret  
ldap.synchronization.queryBatchSize=1000  
ldap.synchronization.attributeBatchSize=1000  
synchronization.synchronizeChangesOnly=false  
synchronization.allowDeletions=true  
synchronization.syncWhenMissingPeopleLogIn=true

ldap.synchronization.groupQuery=objectclass\=group  
ldap.synchronization.groupDifferentialQuery=(&(objectclass\=group)(!(modifyTimestamp<\={0})))

ldap.synchronization.personQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(|(ou=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk),dc=[xx](mailto:s@pucsl.lk))(ou=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk),dc=[xx](mailto:s@pucsl.lk))))

ldap.synchronization.personDifferentialQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(|(ou=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk))(ou=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk),dc=[xxx](mailto:s@pucsl.lk)))(!(modifyTimestamp<\={0})))

ldap.synchronization.groupSearchBase=ou\=[xxx](mailto:s@pucsl.lk),dc\=[xxx](mailto:s@pucsl.lk),dc\=[xxx](mailto:s@pucsl.lk)

ldap.synchronization.userSearchBase=dc\=[xxx](mailto:s@pucsl.lk),dc\=[xxx](mailto:s@pucsl.lk)

ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp  
ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'  
ldap.synchronization.userIdAttributeName=sAMAccountName  
ldap.synchronization.userFirstNameAttributeName=givenName  
ldap.synchronization.userEmailAttributeName=mail  
ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider  
ldap.synchronization.groupDisplayNameAttributeName=displayName  
ldap.synchronization.groupType=group  
ldap.synchronization.personType=user  
ldap.synchronization.groupMemberAttributeName=member  
ldap.synchronization.enableProgressEstimation=true
```


```bash
authentication.chain=alfrescoNtlm1:alfrescoNtlm,ldap-ad1:ldap-ad

ldap.authentication.active=true
ldap.authentication.allowGuestLogin=false
ldap.authentication.userNameFormat=samaccountname=%s,OU=Users,OU=Tap\ Electric,DC=tapelectric,DC=local
ldap.authentication.java.naming.factory.initial=com.sun.jndi.ldap.LdapCtxFactory
ldap.authentication.java.naming.provider.url=ldap://10.20.102.10:389
ldap.authentication.java.naming.security.authentication=simple
ldap.authentication.java.naming.security.principal=samAccountName=mjalan,OU=Users,OU=Tap\ Electric,DC=tapelectric,DC=local
ldap.authentication.java.naming.security.credentials=ComplexHai@2692000
ldap.authentication.escapeCommasInBind=false
ldap.authentication.escapeCommasInUid=false
ldap.authentication.defaultAdministratorUserNames=admin

ldap.synchronization.active=true
ldap.synchronization.java.naming.security.principal=samAccountName=mjalan,OU=Users,OU=Tap\ Electric,DC=tapelectric,DC=local
ldap.synchronization.java.naming.security.credentials=ComplexHai@2692000
ldap.synchronization.queryBatchSize=1000
ldap.synchronization.attributeBatchSize=1000
synchronization.synchronizeChangesOnly=false
synchronization.allowDeletions=true
synchronization.syncWhenMissingPeopleLogIn=true

ldap.synchronization.groupQuery=objectclass\=group
ldap.synchronization.groupDifferentialQuery=(&(objectclass\=group)(!(modifyTimestamp<\={0})))

ldap.synchronization.personQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local))
ldap.synchronization.personDifferentialQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local)(!(modifyTimestamp<\={0})))

ldap.synchronization.groupSearchBase=OU\=Groups,DC\=tapelectric,DC\=local
ldap.synchronization.userSearchBase=OU\=Users,OU\=Tap Electric,DC\=tapelectric,DC\=local

ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp
ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'
ldap.synchronization.userIdAttributeName=samAccountName
ldap.synchronization.groupIdAttributeName=samAccountName
ldap.synchronization.userFirstNameAttributeName=givenName
ldap.synchronization.userEmailAttributeName=userprincipalname
ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider
ldap.synchronization.groupDisplayNameAttributeName=displayName
ldap.synchronization.groupType=group
ldap.synchronization.personType=user
ldap.synchronization.groupMemberAttributeName=member
ldap.synchronization.enableProgressEstimation=true

```





```
ldap.authentication.java.naming.security.principal=CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local

ldap.authentication.java.naming.security.credentials=simpe

```
- These are the ldap bind username and password

```
ldap.authentication.escapeCommasInBind=false
ldap.authentication.escapeCommasInUid=false

```
- this tell if we wnat to keep , in username and password on bind.


```
defaultAdministratorUserNames : admin
```
- these are users that are admin regardless if present in ldap.
```
synchronization.syncWhenMissingPeopleLogIn=true
```
- "If a user tries to log in and they're not already present in the Alfresco user database, go ahead and fetch (sync) their details from LDAP (Active Directory) at that moment."

```
ldap.synchronization.groupQuery=objectclass\=group
ldap.synchronization.groupDifferentialQuery=(&(objectclass\=group)(!(modifyTimestamp<\={0})))

```
- `objectclass=group`  
    This tells Alfresco to look for **LDAP entries of type `group`**, which is the standard object class for AD security groups and distribution lists.
    
- `objectclass\=group`  
    The backslash (`\=`) is used to **escape the equals sign** in `.properties` files — it’s still interpreted as `objectclass=group` at runtime.



Dropping the grup related syn as we dont have grup in the db. for user we have attribure instead in the user that we want to define as grup.


#### **personQuery**

properties

CopyEdit

`ldap.synchronization.personQuery=(&(objectclass=user)(userAccountControl:1.2.840.113556.1.4.803:=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local))`

- **Purpose:** This query is used to retrieve **active users** from the **OU=Users** within **OU=Tap Electric**.
    
- **Explanation:** The filter is looking for **users** (objectclass=user) who are **enabled** (userAccountControl=512).
    
- **`OU=Users,OU=Tap Electric,DC=tapelectric,DC=local`:** This specifies the **organizational unit** and domain for which users should be synced.
    

#### 2. **personDifferentialQuery**

properties

CopyEdit

`ldap.synchronization.personDifferentialQuery=(&(objectclass=user)(userAccountControl:1.2.840.113556.1.4.803:=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local)(!(modifyTimestamp<={0})))`

- **Purpose:** This query retrieves users from the same **OU** who have been modified since the last synchronization.
    
- **Explanation:** It ensures that only modified or newly added users are synced, reducing unnecessary updates.
    

#### 3. **userSearchBase**

properties

CopyEdit

`ldap.synchronization.userSearchBase=OU=Users,OU=Tap Electric,DC=tapelectric,DC=local`

- **Purpose:** This is the search base for users.
    
- **Explanation:** It ensures the synchronization only pulls users from the **Users** OU within the **Tap Electric** domain.
    

#### 4. **modifyTimestampAttributeName**

properties

CopyEdit

`ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp`

- **Purpose:** This specifies the attribute used to track modifications to a user record in AD.
    
- **Explanation:** It is essential for differential syncing (only syncing modified users) and helps track changes.
    

#### 5. **timestampFormat**

properties

CopyEdit

`ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'`

- **Purpose:** Defines the timestamp format for synchronization.
    
- **Explanation:** It ensures the timestamp for the `modifyTimestamp` attribute is parsed correctly.
    

#### 6. **userIdAttributeName**

properties

CopyEdit

`ldap.synchronization.userIdAttributeName=samAccountName`

- **Purpose:** This specifies that the `samAccountName` attribute should be used as the unique identifier for users.
    
- **Explanation:** It’s the typical identifier for a user in Active Directory and will be used during synchronization.
    

#### 7. **userFirstNameAttributeName**

properties

CopyEdit

`ldap.synchronization.userFirstNameAttributeName=givenName`

- **Purpose:** Specifies that the **givenName** attribute should be used for the user's first name.
    
- **Explanation:** This is correct if you want to sync the user's first name.
    

#### 8. **userEmailAttributeName**

properties

CopyEdit

`ldap.synchronization.userEmailAttributeName=userprincipalname`

- **Purpose:** Specifies that the **userPrincipalName** should be used for the user's email address.
    
- **Explanation:** This is typical for Active Directory setups, as the **userPrincipalName** often matches the user's email address.
    

#### 9. **defaultHomeFolderProvider**

properties

CopyEdit

`ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider`

- **Purpose:** Specifies the provider for creating home folders for users.
    
- **Explanation:** This is part of your directory configuration if you want to create home folders upon user sync. Ensure `largeHomeFolderProvider` is properly defined in your system.
    

#### 10. **personType**

properties

CopyEdit

`ldap.synchronization.personType=user`

- **Purpose:** Defines that you are syncing **users**.
    
- **Explanation:** This is the default and is correctly set for syncing users.
    

#### 11. **enableProgressEstimation**

properties

CopyEdit

`ldap.synchronization.enableProgressEstimation=true`

- **Purpose:** Enables progress estimation during the synchronization process.
    
- **Explanation:** This is useful for tracking sync progress.


--- 



```
authentication.chain=alfrescoNtlm1:alfrescoNtlm,ldap-ad1:ldap-ad

ldap.authentication.active=true
ldap.authentication.allowGuestLogin=false
ldap.authentication.userNameFormat=samaccountname=%s,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local

ldap.authentication.java.naming.factory.initial=com.sun.jndi.ldap.LdapCtxFactory
ldap.authentication.java.naming.provider.url=ldap://10.20.102.10:389
ldap.authentication.java.naming.security.authentication=simple

ldap.authentication.java.naming.security.principal=CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
ldap.authentication.java.naming.security.credentials=ComplexHai@2692000

ldap.authentication.escapeCommasInBind=false
ldap.authentication.escapeCommasInUid=false
ldap.authentication.defaultAdministratorUserNames=admin

ldap.synchronization.active=true
ldap.synchronization.java.naming.security.principal=CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
ldap.synchronization.java.naming.security.credentials=ComplexHai@2692000
ldap.synchronization.queryBatchSize=1000
ldap.synchronization.attributeBatchSize=1000
synchronization.synchronizeChangesOnly=false
synchronization.allowDeletions=true
synchronization.syncWhenMissingPeopleLogIn=true


ldap.synchronization.personQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local))
ldap.synchronization.personDifferentialQuery=(&(objectclass\=user)(userAccountControl\:1.2.840.113556.1.4.803\:\=512)(OU=Users,OU=Tap Electric,DC=tapelectric,DC=local)(!(modifyTimestamp<\={0})))

ldap.synchronization.userSearchBase=OU\=Users,OU\=Tap Electric,DC\=tapelectric,DC\=local

ldap.synchronization.modifyTimestampAttributeName=modifyTimestamp
ldap.synchronization.timestampFormat=yyyyMMddHHmmss'.0Z'
ldap.synchronization.userIdAttributeName=samAccountName
ldap.synchronization.userFirstNameAttributeName=givenName
ldap.synchronization.userEmailAttributeName=userprincipalname
ldap.synchronization.defaultHomeFolderProvider=largeHomeFolderProvider
ldap.synchronization.personType=user
ldap.synchronization.enableProgressEstimation=true
```
last checked file
https://connect.hyland.com/t5/alfresco-forum/ldap-ad-subsystem-sync-error/td-p/109244

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
ldap.synchronization.attributeBatchSize=1000
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
ldap.synchronization.enableProgressEstimation=true
```







