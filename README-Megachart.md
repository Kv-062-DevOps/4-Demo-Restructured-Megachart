# megachart
Megachart to deploy all our not megacharts

First of all, you need to update your dependencies. This can be done by calling 
```
helm dep update
```

Make sure, that you have done all the instructions from ecr.md.

Then, you are all set and you are ready to install the MEGACHART. This can be done by the following command which is longer than The Great Wall of China: 
```
helm install test . \
--set registry-creds.ecr.enabled=true \
--set registry-creds.ecr.awsAccount=074368059797 \
--set registry-creds.ecr.awsRegion=eu-central-1 \
--set registry-creds.ecr.awsAccessKeyId="access-key-id-of-the-pulling-user" \
--set registry-creds.ecr.awsSecretAccessKey="secret-access-key-of-the-pulling-user" \
--set registry-creds.ecr.awsAssumeRole=arn:aws:iam::074368059797:role/ecr-access \
--set back.access_key="access-key-of-user-who-can-access-dynamodb" \
--set back.secret_key="secret-key-of-user-who-can-access-dynamodb" \
--set back.region="region-of-dynamodb" \
--set grafana.adminPassword="grafana-admin-password" \
--set-file prometheus.extraScrapeConfigs=extraScrapeConfigs.yaml \
--set-file grafana.dashboards.default.Demo-Dashboard.json=dashboard.json
```

Congratulations! 
