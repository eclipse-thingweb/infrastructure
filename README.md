# Infrastructure

Main infrastructure configuration of the server to manage the deployment of the Eclipse Server.
This repository consists of docker compose files to run Portainer and other infrastructural services such as Traefik proxy, cAdvisor, Prometheus, Grafana and Grafana Loki.

For the list of open ports, see [ports.md](./ports.md)

## Portainer

Portainer is used to manage running Docker containers.

## Infrastructural Services

[docker-compose-services.yml](./docker-compose-services.yml) contains the configuration for the deployment of the infrastructural services.

Set the environment variable `CONFIG_FILEPATH` to the location of the `conf` folder on your computer. This folder is found in the root of this repository.

To be able to access the services, the user must login through GitHub. For GitHub authentication to work, environment variables `OAUTH_SECRET` (can be any string) and, `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` must be set with the configuration of GitHub OAuth application. Only whitelisted emails can access some of the services. Whitelisted emails can be set using the environment variable `WHITELISTED_EMAILS`. These services are accessible at:

- Traefik dashboard -> traefik.localhost
- cAdvisor -> cadvisor.localhost
- Prometheus -> prometheus.localhost

Grafana and Portainer UIs are public access but they run their own authentication and authorization. These services are accessible at:

- Grafana -> grafana.localhost and <http://grafana.plugfest.thingweb.io>
- Portainer -> portainer.localhost and <http://plugfest.thingweb.io:8089/>

Hostname and ports can be changed from `.env` file in the root directory.

## Saving Grafana Dashboards

Grafana dashboard json files are stored in [./conf/grafana/dashboards](./conf/grafana/dashboards/).
To save your newly created dashboard locally and push it into the remote repository:

- Export the dashboard as JSON file using Share > Export.
- Save the exported JSON file to [./conf/grafana/dashboards](./conf/grafana/dashboards/).

If your dashboard uses another datasource than our default `prometheus-datasource`, new datasource also must be provisioned in [./conf/grafana/datasources](./conf/grafana/provisioning/datasources/).
For more information check Grafana's provisioning [documentation](https://grafana.com/docs/grafana/latest/administration/provisioning/).

## Instructions

1. After deploying Grafana, configure GitHub OAuth2 through developer settings
2. Add emails for admin rights via role attributes: `[email==<USER_EMAIL>] && 'Admin' || 'Viewer'`

## Domus TDD

The [domus TD Directory](https://github.com/eclipse-thingweb/domus-tdd-api) is started via its own stack.
The port and domain are hard-coded and should be changed accordingly in the YAML file.
The API is available through `http://plugfest.thingweb.io:8081`, e.g. `http://plugfest.thingweb.io:8081/things` will return all the TDs.
