# Application Initialization

- [ ] If the project is not a Grails project, stop here.
- [ ] Verify that the following dependency is present in `build.gradle`: `implementation "org.apache.grails:grails-core"`. If it is missing, tell the user this is not a Grails project and stop here.
- [ ] Add the following dependency to `build.gradle`: `implementation "org.goowee:goowee-core:2.0.0"`.
- [ ] If you cannot create a Goowee project stop here.
- [ ] Add the following code to initialize the application and create the TenantInstallService with an install() method:

```groovy
class BootStrap {

    GooweeApplication gooweeApplication
    TenantInstallService tenantInstallService

    def init = {
        gooweeApplication.onTenantInstall { Stirng tenantId ->
            tenantInstallService.install()
        }
        
        gooweeApplication.onInit {
            // Register features, prettyPrinters, credits
        }
    }
    
}
```

- [ ] Create the following files:
  - `grails-app/assets/javascripts/goowee.js`
  - `grails-app/assets/stylesheets/goowee.css`

- [ ] Add the logging configuration to `application.yml` replacing `${project-name}` with the project name:
```yaml
---
logging:
  level:
    root: ERROR
    org.springframework.boot.SpringApplication: INFO
    org.springframework.boot.StartupInfoLogger: INFO
    goowee: DEBUG
    ${project-name}: INFO
    # goowee.commons.utils.SqlUtils: TRACE
    # goowee.ImportUtils: TRACE
    # org.grails.datastore: DEBUG
    # org.hibernate.SQL: DEBUG
    # org.hibernate.type.descriptor.sql.BasicBinder: TRACE
    # org.springframework.security: DEBUG
    # grails.plugin.springsecurity.web.filter.DebugFilter: INFO
    # sun.net.www.protocol.http.HttpURLConnection: ALL
  file:
    name: ${info.app.name}/logs/${info.app.name}.log
  logback:
    rollingpolicy:
      file-name-pattern: ${info.app.name}/logs/archive/${info.app.name}.%d{yyyy-MM-dd}.%i.log.zip
      clean-history-on-start: true
      max-history: 10
      max-file-size: 10MB
      total-size-cap: 100GB
  pattern:
    # Logback highlights ERROR in bold red and WARN in red; make plain red yellow and INFO default.
    console: "\u001B[90m%d{HH:mm:ss.SSS}\u001B[39m %replace(%replace(%highlight(%-5level)){'\\u001B\\[31m','\u001B[33m'}){'\\u001B\\[(32|34|35)m','\u001B[39m'} \u001B[90m[%thread]\u001B[39m \u001B[90m%-40.40logger{36}\u001B[39m \u001B[90m:\u001B[39m %replace(%replace(%highlight(%msg%n)){'\\u001B\\[31m','\u001B[33m'}){'\\u001B\\[(32|34|35)m','\u001B[39m'}"
    file: '%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %-40.40logger{36} : %msg%n'
```

- [ ] Add the following configuration to `application.yml`, replacing `${project-name}` with the project name:
```yml
---
server:
  tomcat:
    basedir: ${project-name}/tomcat
  servlet:
    session:
      persistent: true
      store-dir: ${project-name}
  compression:
    enabled: true
    mime-types: text/html,text/xml,text/plain,text/css,text/javascript,application/javascript,application/json

---
javamelody:
  init-parameters:
    log: true
    storage-directory: ${user.dir}/${project-name}/java-melody

---
spring:
  main:
    banner-mode: console
  threads:
    virtual:
      enabled: true
  h2:
    console:
      enabled: true
  servlet:
    multipart:
      maxFileSize: 20MB
      maxRequestSize: 20MB
```

- [ ] Set the H2 database URL to `jdbc:h2:./project-name/project-name;LOCK_TIMEOUT=10000;DB_CLOSE_ON_EXIT=FALSE`.

- [ ] Set the `dbCreate` property to `update` for the development environment.

- [ ] Add `/project-name/` to the root `.gitignore`.

- [ ] Copy the `messages.properties` file from the assets to `grails-app/i18n/messages.properties`.
