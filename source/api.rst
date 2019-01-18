.. toctree::

API
---

It's possible to do all operations using the Onedata API.

The official documentation is: https://onedata.org/#/home/api.

.. important:: In order to be able to access the `Onedata APIs`, it's required
    to generate an access token.

Getting an API access token
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Tokens have to be generated from the `DataHub` (Onezone) interface as
documented in :ref:`auth-token-using-web-interface` or using a command line
call as documented hereafter.

The following variables can be exported:

* `OIDC_TOKEN`: OpenID Connect Access token, see
  https://wiki.egi.eu/wiki/Federated_Cloud_OpenStack_Providers#Obtaining_an_access_token
  for obtaining it.
* `ONEZONE_HOST`: name or IP of the Onezone host (to use Onezone API).
* `ONEPROVIDER_HOST`: name or IP of the Oneprovider host (to use Oneprovider API).

.. code-block:: console

   export ONEZONE_HOST=datahub.egi.eu
   export OIDC_TOKEN=<OIDC_ACCESS_TOKEN>
   curl -H "X-Auth-Token: egi:$OIDC_TOKEN" -X POST \
     -H 'Content-type: application/json' -d '{}' \
     https://$ONEZONE_HOST/api/v3/onezone/user/client_tokens

Registering a Handle for a file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Prerequisites: access to a Handle service registered in the Onezone.
See
https://onedata.org/#/home/documentation/doc/using_onedata/handle_services.html
for documentation on registering a new Handle service or ask a Onezone
administrator to authorize you to use an existing Handle service already
registered in the Onezone.


The following variables should be exported:

* `API_ACCESS_TOKEN`: Onedata API access token
* `ONEZONE_HOST`: name or IP of the Onezone host (to use Onezone API).

.. code-block:: console

   # Getting the IDs of the available Handle Services
   curl -sS --tlsv1.2 -H "X-Auth-Token: $API_ACCESS_TOKEN" \
     -X GET \
     "https://datahub.egi.eu/api/v3/onezone/user/handle_services"
   export HANDLE_SERVICE=<HANDLE_SERVICE_ID>
   # Getting details about a specific Handle service
   curl -sS --tlsv1.2 -H "X-Auth-Token: $API_ACCESS_TOKEN" \
     -X GET \
     "https://$ONEZONE_HOST/api/v3/onezone/user/handle_services/$HANDLE_SERVICE"
   # Getting the ID of a space or directory of a space
   # TO BE DONE
   export RESOURCE=<RESOURCE_ID>
   # Registering a handle
   curl -sS --tlsv1.2 -H "X-Auth-Token: $API_ACCESS_TOKEN" \
     -H "Content-type: application/json" \
     -X POST \
     -d '{"handleServiceId": "$HANDLE_SERVICE", "resourceType": "Share", "resourceId": "$RESOURCE", "metadata": "..." }' \
     https://$ONEZONE_HOST/api/v3/handles
