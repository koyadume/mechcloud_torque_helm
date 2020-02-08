## Installing oauth2-proxy
* Clone this repository.
* Installation -
```
cd mechcloud_torque_helm
helm install \
--set=oauth2.clientId=<Client ID>,oauth2.clientSecret=<Client Secret>,oauth2.cookieSecret=<Cookie Secret> \
torque .
```