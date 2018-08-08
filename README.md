# JIRA
Docker image for Atlassian JIRA. It includes all dependencies, listed in the Atlassian's "supported platforms" page, except a database. Please link a database by yourself.

## Docker stop timeout
Please note that default timeout of docker stop is 10s, but Jira may take more time. To make sure Jira doesn't get killed:

    docker stop -t 120 container

You can also override the default stop timeout in `docker run` once when creating the container. See example below.

## Volumes
This image does not define any volumes to prevent "anonymous" volumes phenomenon. It's recommended to mount these volume path:

  * `/var/atlassian/application-data/jira`

## Exposed ports
This image exposes `tcp/8080`.

## Environment variables
Find below all environment variables and its defaults.

`CATALINA_CONNECTOR_PROXYNAME=`
The reverse proxy's fully qualified hostname.

`CATALINA_CONNECTOR_PROXYPORT=`
The reverse proxy's port number via which JIRA is accessed.

`CATALINA_CONNECTOR_SCHEME=`
The protocol via which JIRA is accessed.

`CHECK_LOCK_FILE=true`
If set, will check for JIRA lock file at startup. If lock file is present, startup will be prevented. The check will be done every second.

# Example usage

    docker run -tid --env CHECK_LOCK_FILE=false --stop-timeout=120 \
      -v jira-data:/var/atlassian/application-data/jira \
      --name=test mimacom/jira:latest
