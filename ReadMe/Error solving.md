

compose share app

2025-04-11 16:01:16.454 WARN (Thread-11) [ x:alfresco] o.a.s.c.Config XML parse warning in "solrres:/solrconfig.xml", line 1858, column 88: Include operation failed, reverting to fallback. Resource error reading file as XML (href='solrconfig_insight.xml'). Reason: Can't find resource 'solrconfig_insight.xml' in classpath or '/opt/alfresco-search-services/solrhome/alfresco'


-Dorg.apache.catalina.webresources.cache.maxSize=131072
add this to share:
```yaml

share:

image: docker.io/alfresco/alfresco-share:25.1.0

mem_limit: 1g

environment:

CSRF_FILTER_ORIGIN: http://localhost:8080

CSRF_FILTER_REFERER: http://localhost:8080/share/.*

REPO_HOST: "alfresco"

REPO_PORT: "8080"

JAVA_OPTS: >-

-XX:MinRAMPercentage=50

-XX:MaxRAMPercentage=80

-Dalfresco.host=localhost

-Dalfresco.port=8080

-Dalfresco.context=alfresco

-Dalfresco.protocol=http

-Dorg.apache.catalina.webresources.cache.maxSize=131072

```
---
2025-04-11 17:16:11.622 WARN (Thread-11) [ x:alfresco] o.a.s.c.Config XML parse warning in "solrres:/solrconfig.xml", line 1858, column 88: Include operation failed, reverting to fallback. Resource error reading file as XML (href='solrconfig_insight.xml'). Reason: Can't find resource 'solrconfig_insight.xml' in classpath or '/opt/alfresco-search-services/solrhome/alfresco'


opt/alfresco-search-service/solrhome/conf/solrconfig_insight.xml

- The **Insight Engine** (which uses `solrconfig_insight.xml`) is **only available in the Alfresco Enterprise Edition**.

- The **Insight Engine** (which uses `solrconfig_insight.xml`) is **only available in the Alfresco Enterprise Edition**.
    
- In the **Community Edition**, this feature is not active or needed.
    
- So if Solr is trying to load that file and can’t find it — and you're not using any Insight-related features — it's best to **just remove or comment out the include** from `solrconfig.xml`.

---




