# [OpenIMIS](https://github.com/openimis) 

Minimum set of components for [Sandbox](https://github.com/GovStackWorkingGroup/sandbox):

* Database
* Backend
## [Database](https://github.com/openimis/database_postgresql) 

Backend expects database with predefine schema and data.

Custom [Dockerfile](https://github.com/openimis/database_postgresql/blob/main/Dockerfile) provides necessary DB.

## [Backend](https://github.com/openimis/openimis-be_py.git)

Backend expects communication via Gateway component.

### API

* [FHIR](https://en.wikipedia.org/wiki/Fast_Healthcare_Interoperability_Resources) standard
* Swagger API [documentation](https://dev-mssql.s1.openimis.org/api/api_fhir_r4/docs/swagger/) 


## Docker images

Docker images are organized based on [infra repository](https://github.com/GovStackWorkingGroup/sandbox-infra).

## Useful commands

* `helm upgrade --install sandbox-open-imis ./sandbox-open-imis/ --create-namespace --namespace open-imis`

* `helm install --debug --dry-run sandbox-open-imis ./sandbox-open-imis/`

### X-Road connection 

Port forward
* `kubectl port-forward service/govstack-xroad-ssp 8000:4000 -n govstack`
* `kubectl port-forward service/govstack-xroad-ssc 7000:4000 -n govstack`
* `kubectl port-forward service/backend 8001:8000 -n open-imis`

Service endpoint
* `http://backend.open-imis.svc.cluster.local:8000/api_fhir_r4`

Log into pod
* `kubectl exec -it pod/{pod name} -n govstack -- bash`

Get auth token
* `curl -XPOST -H 'X-Road-Client: DEV/GOV/111/CONSUMER' -H "Content-type: application/json" -d '{ "username": "", "password": "" }' 'http://localhost:8080/r1/DEV/GOV/222/PROVIDER/open-imis/login/'`

Get Contract data
* `curl -XGET
-H 'X-Road-Client: DEV/GOV/111/CONSUMER'
-H "Content-type: application/json" 
-H "Authorization: Bearer {token}"
'http://localhost:8080/r1/DEV/GOV/222/PROVIDER/open-imis/Contract/'`