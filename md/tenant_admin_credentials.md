# Tenant administrator credentials

Each tenant has an administrator, with a tenant-specific username and password. The **tenant administrator** is also known as the **tenant technical user**.

## How it works
When the platform is created, default values of the administrator username and password, for the default tenant, are defined in the file
`<WEBSERVER_HOME>/setup/platform_conf/initial/tenant_template_engine/bonita-tenant-community-custom.properties`, by the following properties:

* userName defines the username (default value `install`)
* userPassword defines the password (default value `install`)

If you modify these values before the first start of the platform, the new values will be the default values for all tenants that will be
created in the future, including the default tenant.

When you create a tenant, or when the default tenant is created on the first start of the platform, the tenant administrator is created
with the default username and password, unless you specify new values.

For an already existing tenant, you can change these tenant-specific credentials by updating the *userName* and *userPassword* properties in the file

`<WEBSERVER_HOME>/setup/platform_conf/current/tenants/<TENANT_ID>/tenant_engine/bonita-tenant-community-custom.properties`


## Important notice (only for default tenant)
The engine and the portal can be installed on different machines / Tomcat / WildFly installations. For that reason, the portal has its own configuration file
that define the tenant technical user credentials, in order to communicate with the (potentially remote) engine.

For this matter, if you change the tenant admin credentials (default tenant only) on engine side (see above), you must also update the corresponding values in the file:
`<WEBSERVER_HOME>/setup/platform_conf/`**initial**`/platform_portal/platform-tenant-config.properties` if you have never started the platform yet, and
`<WEBSERVER_HOME>/setup/platform_conf/`**current**`/platform_portal/platform-tenant-config.properties` if the platform has been already started.