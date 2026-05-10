# Continous Deployment Resources 

Compose files used by Ansible to deploy resources. 

## Compose 

Compose is organized into sub files and resources and inherited into a main compose file that imports them. 

### Operations 

Traefik

### Monitoring

Full monitoring and alerting stack 

- Grafana 
- Loki
- Mimir
- Crowdsec 

### Storage 

MongoDB 

### Applications 

Applications built on GHCR.io

### Media

Media tooling

## Ansible

Ansible syncs this repository looking for changes and applies them if a change is found using `docker compose up -d` 

## Updates

Renovate watches this repository and makes PRs on changes which get applied to a staging server and then merges to the main server if successful