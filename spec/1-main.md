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