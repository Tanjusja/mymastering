# mymastering
working repository for mymastering.ru

Needed:
  Maven, WildFly, PostgreSQL
 
 
Module in WildFly:

  <?xml version="1.0" encoding="UTF-8"?>
<module xmlns="urn:jboss:module:1.3" name="org.postgresql">
    <resources>
        <resource-root path="postgresql-42.2.1.jar"/>
        <!-- Make sure this matches the name of the JAR you are installing -->
    </resources>
    <dependencies>
        <module name="javax.api"/>
        <module name="javax.transaction.api"/>
    </dependencies>
</module>


Standalone.conf

  <drivers>
    <driver name="postgresql" module="org.postgresql">
        <!-- for xa datasource -->
        <xa-datasource-class>org.postgresql.xa.PGXADataSource</xa-datasource-class>
        <!-- for non-xa datasource -->
        <driver-class>org.postgresql.Driver</driver-class>
    </driver>
</drivers>

<datasources>
    <datasource jndi-name="java:jboss/datasources/StenusysDemoDS" pool-name="StenusysDemoDS" enabled="true" use-java-context="true">
        <connection-url>jdbc:postgresql://localhost:5432/StenusysDemo</connection-url>
        <driver>postgresql</driver>
        <security>
            <user-name>postgres</user-name>
            <password>admin</password>
        </security>
    </datasource>
</datasources>


jdbc 4.2.2, postgres 10, wildfly 12
