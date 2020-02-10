## 
## Deploying Torque
* Make sure [helm 3](https://helm.sh/docs/intro/install) client is installed in an environment where you will be executing these instructions from.
* Clone this repository.
```
git clone git@github.com:mechcloud/mechcloud_torque_helm.git
```

## Deployment options
### Deploying with auth disabled
* This is recommended for local or any other environment which can be accessed by you or your team ONLY.
* Execute following commands to deploy torque -
```
cd mechcloud_torque_helm
helm install --set=authEnabled=false torque .
```

### Deploying with auth enabled
* Update values in `mechcloud_torque_helm/values.yaml` file as per your target deployment.
  * This app uses [oauth2_proxy](https://pusher.github.io/oauth2_proxy) to secure it using an oauth2 provider.
  * Addtional configuration parameters (`githubOrg`, `githubTeam`) under `oauth2` section of `mechcloud_torque_helm/values.yaml` file are specific to `github` as oauth2 provider.
  * If you are using `github` as oauth2 provider and deploying to [Okteto Cloud](https://cloud.okteto.com), you just need to update values in `mechcloud_torque_helm/values.yaml` file as per your needs.
    * For registering an oauth app on github, use https://github.com/settings/applications/new link and specify values for different parameters as following (Update FQDN below as per your target deployment) -
      * **Application Name** - Torque
      * **Homepage URL** - https://torque.cloud.okteto.net
      * **Authorization callback URL** - https://torque.cloud.okteto.net/oauth2/callback
  * For any other combination refer [oauth2_proxy](https://pusher.github.io/oauth2_proxy) and your target deployment environment documentation. 
* Execute following commands to deploy torque -
```
cd mechcloud_torque_helm
helm install --set=torqueNamespace=<target namespace> torque .
```

