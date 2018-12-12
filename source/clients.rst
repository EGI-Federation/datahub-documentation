.. toctree::

Clients
-------

Testing Oneclient in a Vagrant box
``````````````````````````````````

It's possible to quickly test Oneclient using `Vagrant <https://www.vagrantup.com/>`_.

In order to be able to access your spaces using `Oneclient` or `APIs`, it's
required to generate an access token.

Tokens have to be generated from the `DataHub` (Onezone) interface.

The following variables have to be exported:

* `ONECLIENT_ACCESS_TOKEN`: access token allowing to access **all** the spaces.
* `ONECLIENT_PROVIDER_HOST`: name or IP of the Oneprovider the client should connect to.

.. image:: _static/datahub-space-token.png

.. code-block:: console

   vagrant init ubuntu/xenial64
   vagrant up
   vagrant ssh
   curl -sS http://get.onedata.org/oneclient.sh | bash
   export ONECLIENT_ACCESS_TOKEN=<ACCESS_TOKEN_FROM>
   export ONECLIENT_PROVIDER_HOST=plg-cyfronet-01.datahub.egi.eu
   mkdir /tmp/space
   oneclient /tmp/space
