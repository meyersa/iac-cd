# Continous Deployment Resources

Compose files used by Ansible to deploy resources.

## Docker Compose

Deployment resources are grouped by component in a compose file. Using this compose file, an "we have Argo at home" approach can be used for managing projects without the overhead of Kubernetes.

Using options like remove orphans and recreate, this directory can be expanded out to manage all resources.

TODO: In the future, use `docker ps` to build a list of containers and reconcile Docker to parity Argo prune

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

| Alert                 | Scope     | Channel | Source  | Purpose                                                                          |
| --------------------- | --------- | ------- | ------- | -------------------------------------------------------------------------------- |
| Host Up               | Host      | Alerts  | Grafana | When a host goes up or down                                                      |
| Host Errors           | Host      | Alerts  | Grafana | When a host has a large amount of error logs in JournalCTL                       |
| Host CPU              | Host      | Alerts  | Grafana | Host high CPU usage                                                              |
| Host Memory           | Host      | Alerts  | Grafana | Host high memory usage                                                           |
| Host Storage          | Host      | Alerts  | Grafana | Host low storage remaining                                                       |
| SSH Login             | Host      | Info    | Grafana | When someone SSHs in to the server                                               |
| Container restarting  | Container | Alerts  | Grafana | When a container is restarting                                                   |
| Container errors      | Container | Alerts  | Grafana | When a container is erroring                                                     |
| Container HTTP Errors | Container | Alerts  | Grafana | When a container has a high percentage of HTTP errors relative to normal traffic |
| Container HTTP Status | Container | Alerts  | Grafana | When a container's web status goes up or down                                    |

| Crowdsec Action | Environment | Info | Crowdsec | When an attack is detected |

TODO: See if Crowdsec actions can be grouped, or instead alerted through Grafana so it can be handled better

| Dashboard | Target | Purpose |

#### External Alerts

In the case that Grafana itself goes down, it's monitored externally by UptimeRobot
TODO: Switch UptimeRobot -> Oracle Cloud Alerting

### Storage

Storage instances

- MongoDB

### Applications

Applications built on GHCR.io

### Media

TODO: Setup resources for managing media and debrid

- Sonarr
- Radarr
- Prowlarr
- Buildarr
- Jellyfin?

## Updates

TODO: Switch to specific containers and setup renovate to watch them
TODO: Setup CI for renovate updates to apply them to `dev` and health check the server before auto merging (GitHub build post)
