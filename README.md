_Archiving for now, because will be soon moved to https://github.com/humanitec-architecture/resource-packs-in-cluster._

# mongodb-in-cluster-as-resource

```bash
export HUMANITEC_ORG=FIXME
export HUMANITEC_TOKEN=FIXME
```

As Platform Admin, define an in-cluster `mongodb` resource:
```bash
humctl create \
    -f mongodb-incluster-resource.yaml
```

As Developer, deploy the frontend app talking to the `mongodb` resource:
```bash
ENVIRONMENT=development
MONGO_APP=your-mongo-app

score-humanitec delta \
    --deploy \
    --app ${MONGO_APP} \
    --env ${ENVIRONMENT} \
    --org ${HUMANITEC_ORG} \
    --token ${HUMANITEC_TOKEN} \
    --retry \
    -f score.yaml
```
