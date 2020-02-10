## Deploying Torque
* Make sure [helm 3](https://helm.sh/docs/intro/install) client is installed in an environment where you will be executing these instructions from.
* Clone this repository.
```
git clone git@github.com:mechcloud/mechcloud_torque_helm.git
```
* Update values in `mechcloud_torque_helm/values.yaml` file as per your deployment.
  * This app uses [oauth2_proxy](https://pusher.github.io/oauth2_proxy) to secure it using an oauth2 provider.
  * Addtional configuration parameters (`githubOrg`, `githubTeam`) under `oauth2` section of `mechcloud_torque_helm/values.yaml` file are specific to `github` as oauth2 provider.
  * If you are using `github` as oauth2 provider and deploying to [Okteto Cloud](https://cloud.okteto.com), you just need to update values in `mechcloud_torque_helm/values.yaml` file as per your needs.
    * For registering an oauth app on github, use https://github.com/settings/applications/new link and specify values as following (Update FQDN of torque as per your deployment) -

| Parameter Name| Parameter Value |
| ------------- |-------------|
| Application Name | MechCloud Torque |
| Homepage URL | https://torque-koyadume.cloud.okteto.net |
| Authorization callback URL | https://torque-koyadume.cloud.okteto.net/oauth2/callback |

  * For any other combination refer [oauth2_proxy](https://pusher.github.io/oauth2_proxy) and your target deployment environment documentation. 
* Installation -
```
cd mechcloud_torque_helm
helm install torque .
```

