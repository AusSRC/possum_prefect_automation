This is backup to setup Prefect v3 self-hosted server with OAuth2-Proxy using docker.

OAuth2-Proxy supports many providers (https://oauth2-proxy.github.io/oauth2-proxy/configuration/providers/). 
We use GitHub for Possum.

Basically:
1. In the possum configuration, we added extra config for oauth2-proxy in the docker-compose.yaml. 
2. On the GitHub side, you set up the secrets and redirect URI when you go to developer settings. 
The secrets are then passed on to the docker-compose on the prefect server side.
3. Set up nginx to make sure the redirect and callbacks are working.

More info: https://oauth2-proxy.github.io/oauth2-proxy/

Please note, the OAuth2-Proxy is mainly for UIs, and is not API friendly, e.g. if using the domain protected by OAuth2, you will not be able to run flows programmatically.
The solution is to use the direct IP address and auth string for the Prefect server for the flows. The external domain is strictly used for the web UI.

For example in the possum config.env, we'd have:

* PREFECT_API_URL=http://xx.xxx.xx.xxx:4200/api
* PREFECT_API_AUTH_STRING=admin:secretpassword

Please note, PREFECT_API_AUTH_STRING is used on the client side, and this corresponds to PREFECT_SERVER_API_AUTH_STRING on the server side.

To manage the flows from the web UI, we use possum-prefect.aussrc.org. 

To resolve the possum-prefect.aussrc.org URL, we added Proxied (orange) DNS entry in Cloudflare. 

To start Prefect container:

* cd to the location of docker-compose.yaml

* `docker compose up -d`

To reload Nginx after config changes:

`sudo systemctl reload nginx`

