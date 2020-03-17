## H2 JBOSS WRAPPER
Application that creates a wrapper for **H2Console** into a `*.war` file to access in-memory database from **Wildfly/Jboss**.

#### HOW-TO
Follow these steps to get it running:
- Declare the H2 Module: `~/jboss-as/modules/com/h2database/h2/main/module.xml`
```
<?xml version="1.0" encoding="UTF-8"?>
<module xmlns="urn:jboss:module:1.3" name="com.h2database.h2">
  <resources>
    <resource-root path="h2-1.4.190.jar"/>
  </resources>
  <dependencies>
    <module name="javax.api"/>
    <module name="javax.transaction.api"/>
    <module name="javax.servlet.api"/>
  </dependencies>
</module>
```

- Compile the **Application**:
```
cd ~/h2-console-jboss-wildfly
zip -r h2-console-jboss-wildfly.war *
```

- Move the **Application** to **Jboss** and start it:
```
mv ~/h2-console-jboss-wildfly/h2-console-jboss-wildfly.war ~/jboss-as/standalone/deployments
~/jboss-as/bin/./standalone.sh
```

- Access the **Application** from browser:
```
http://localhost:8080/h2-console-jboss-wildfly
JDBC URL: jdbc:h2:mem:process-engine;DB_CLOSE_ON_EXIT=FALSE;DB_CLOSE_DELAY=-1
```