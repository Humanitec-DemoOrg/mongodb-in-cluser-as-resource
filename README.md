# mongodb-in-cluser-as-resource

```bash
export HUMANITEC_ORG=FIXME
export HUMANITEC_TOKEN=FIXME
```

As Platform Admain, define an in-cluster `mongodb` resource:
```bash
yq -o json mongodb-incluster-resource.yaml > mongodb-incluster-resource.json
curl "https://api.humanitec.io/orgs/${HUMANITEC_ORG}/resources/defs" \
    -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer ${HUMANITEC_TOKEN}" \
    -d @mongodb-incluster-resource.json
```

As Developer, deploy the frontend app talking to the `mongodb` resource:
```bash
ENVIRONMENT=development
MONGO_APP=your-mongo-app

score-humanitec delta \
    --app ${MONGO_APP} \
    --env ${ENVIRONMENT} \
    --org ${HUMANITEC_ORG} \
    --token ${HUMANITEC_TOKEN} \
    --retry \
    -f score.yaml \
    --extensions humanitec.score.yaml
```
