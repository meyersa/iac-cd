# Continous Deployment Resources

Compose files used by Ansible to deploy resources.

## Docker Compose

Deployment resources are grouped by component in a compose file. Using this compose file, an "we have Argo at home" approach can be used for managing projects without the overhead of Kubernetes.

Using options like remove orphans and recreate, this directory can be expanded out to manage all resources.

### Operations

Resources related to supporting other resources.

Traefik

### Monitoring

Resources for monitoring and alerting on infrastructure.

- Grafana
- Loki
- Mimir
- Crowdsec
- Maxmind

#### Grafana Logic

| Alert                 | Scope       | Channel | Source   | Purpose                                                                          |
| --------------------- | ----------- | ------- | -------- | -------------------------------------------------------------------------------- |
| Host Up               | Host        | Alerts  | Grafana  | When a host goes up or down                                                      |
| Host Errors           | Host        | Alerts  | Grafana  | When a host has a large amount of error logs in JournalCTL                       |
| Host CPU              | Host        | Alerts  | Grafana  | Host high CPU usage                                                              |
| Host Memory           | Host        | Alerts  | Grafana  | Host high memory usage                                                           |
| Host Storage          | Host        | Alerts  | Grafana  | Host low storage remaining                                                       |
| SSH Login             | Host        | Info    | Grafana  | When someone SSHs in to the server                                               |
| Container restarting  | Container   | Alerts  | Grafana  | When a container is restarting                                                   |
| Container errors      | Container   | Alerts  | Grafana  | When a container is erroring                                                     |
| Container HTTP Errors | Container   | Alerts  | Grafana  | When a container has a high percentage of HTTP errors relative to normal traffic |
| Container HTTP Status | Container   | Alerts  | Grafana  | When a container's web status goes up or down                                    |
| Crowdsec Action       | Environment | Info    | Crowdsec | When an attack is detected                                                       |

| Dashboard  | Target     | Purpose                            |
| ---------- | ---------- | ---------------------------------- |
| Overview   | All        | Show the complete system status    |
| Database   | Datbases   | Show the database health (Mongo)   |
| Hosts      | Hosts      | Show the health of the hosts       |
| Containers | Containers | Show the health of containers      |
| SSH        | All        | Show statistics about security/SSH |
| Web        | Websites   | Show website health and statistics |
| Logs       | Hosts      | Show information about log metrics |

#### External Alerts

In the case that Grafana itself goes down, it's monitored externally by UptimeRobot

### Storage

Storage instances

- MongoDB

### Applications

Applications built on GHCR.io

### Media

- Sonarr
- Radarr
- Prowlarr
- Buildarr
- Jellyfin?

## Updates

On changes to this repository Actions gets triggered and applies the change to the Dev instance. When that suceeds it gets approved to merge to main and get applied on the Prod instance.

Dependabot regularly scans this as well and gets its changes auto-merged into main on success.
