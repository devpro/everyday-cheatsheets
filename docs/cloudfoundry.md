# Cloud Foundry CLI Cheat Sheet

## Command line

`cf version`

`cf --version`

`cf --help`

`cf <command> -h`

`cf login -a <cf-api-endpoint>`

`cf target`

`cf push pal-tracker --random-route -p src/PalTracker/bin/Release/netcoreapp2.1/publish`

`cf set-env pal-tracker WELCOME_MESSAGE "Hello from Cloud Foundry"`

`cf restart pal-tracker`

`cf delete pal-tracker`

`cf map-route`

`cf marketplace`

`cf create-service cleardb spark tracker-database`

`cf bind-service pal-tracker tracker-database`

## Recipes

### Integration with Kubernetes

* [CF for k8s](https://cf-for-k8s.io/)
  * [The New Stack > Using Grafana to Monitor Cloud Foundry Objects and Apps Running on Kubernetes](https://thenewstack.io/using-grafana-to-monitor-cloud-foundry-objects-and-apps-running-on-kubernetes/) - March 5, 2021
