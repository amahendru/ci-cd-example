# CI CD Example Application

## Process
- Create API Instance in API Manager and apply policies. Note down the API Instance ID.
- Update the pom.xml with following details:
  - Update the project.version accordingly
  - Fill api.instance.id with id noted from last step
  - Update rtf related parameters like deploy.rtf.replication_factor etc.

## Deployment to Exchange
mvn clean deploy

## Deployment to RTF Cluster
mvn clean deploy -DmuleDeploy -Dapi.id=18303864 -Dmule.env=dev -Danypoint.connected.app.id=xxxxx -Danypoint.connected.app.secret=xxxxx -Danypoint.client.id=xxxxx -Danypoint.client.secret=xxxx -Ddeploy.rtf_platform_name=test-rtf-eks-cluster -Danypoint.environment=Sandbox -Durl.domain=api.amahendru.com

## Delete from Exchange
curl -X DELETE "https://anypoint.mulesoft.com/exchange/api/v2/assets/$project.groupId/$project.artifactId/$project.version" \
              -H "authorization: bearer $ACCESS_TOKEN" \
              -H "Content-Type: application/json" \
              -H "X-Delete-Type: hard-delete"