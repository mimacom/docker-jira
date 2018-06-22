# JIRA
Docker image for Atlassian JIRA. It includes all dependencies, listed in the Atlassian's "supported platforms" page, except a database. Please link a database by yourself.

## Docker stop timeout
Please note that default timeout of docker stop is 10s, but Jira may take up to
120s. To make sure Jira doesn't get killed:

docker stop -t 120 [container]

## Reverse proxy settings
Use these environment variables, if you want to run a reverse proxy in front of the JIRA service.

 * *CATALINA_CONNECTOR_PROXYNAME*: The reverse proxy's fully qualified hostname. (Default NONE)
 * *CATALINA_CONNECTOR_PROXYPORT*: The reverse proxy's port number via which JIRA is accessed. (Default NONE)
 * *CATALINA_CONNECTOR_SCHEME*: The protocol via which JIRA is accessed. (Default NONE)
