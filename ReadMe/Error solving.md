

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

2025-04-10T20:14:59,012 [] ERROR [framework.webscripts.ResourceWebScriptGet] [http-nio-8080-exec-9] Exception 7c3c5db4-d957-4895-bc5d-b4d957a8953d. Request /alfresco/api/-default-/public/alfresco/versions/1/nodes/-my-?relativePath=config.json executed by user admin returned status code 404 with message: 03100004 The entity with relativePath: config.json was not found. - Increase logging on org.alfresco.rest.framework.webscripts.ResourceWebScriptGet for stack trace.

/home/ubuntu/alfresco-content-app/node_modules/table/dist/src/schemas/config.json

---
docker-compose-solr6-1

2025-04-11 17:16:11.622 WARN (Thread-11) [ x:alfresco] o.a.s.c.Config XML parse warning in "solrres:/solrconfig.xml", line 1858, column 88: Include operation failed, reverting to fallback. Resource error reading file as XML (href='solrconfig_insight.xml'). Reason: Can't find resource 'solrconfig_insight.xml' in classpath or '/opt/alfresco-search-services/solrhome/alfresco'



