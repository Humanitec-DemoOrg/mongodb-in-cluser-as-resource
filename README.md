# mongodb-in-cluser-as-resource

```bash
export HUMANITEC_ORG=FIXME
export HUMANITEC_TOKEN=FIXME
```

```bash
ENVIRONMENT=development

score-humanitec delta \
    --app ${MONGO_APP} \
    --env ${ENVIRONMENT} \
    --org ${HUMANITEC_ORG} \
    --token ${HUMANITEC_TOKEN} \
    --retry \
    -f score.yaml \
    --extensions humanitec.score.yaml
```
