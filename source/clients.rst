.. toctree::

Clients
-------

Using the web interface
^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: _static/datahub-connect-check-in.png
   :alt: EGI DataHub connection with Check-in

   Selecting EGI to connect using EGI Check-in

   Using EGI Check-in it's possible to connect with its institute credentials.

.. figure:: _static/datahub-welcome-screen.png
   :alt: EGI DataHub landing page

   EGI DataHub landing page

   On this page it's possible to have an overview of all the spaces and their
   supporting providers.

.. figure:: _static/datahub-space-info.png
   :alt: EGI DataHub spaces information

   Information about spaces supported by a Oneprovider

   On this capture, the information about the spaces supported
   by a specific provider is displayed.

.. figure:: _static/datahub-browse-space.png
   :alt: EGI DataHub browsing a space

   Information about spaces supported by a Oneprovider

   The data space can be managed (ie. uploading/downloading/managing files and
   metadata, manging space access) using the web browser.


Generating tokens for using Oneclient or APIs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. important:: In order to be able to access your spaces using `Oneclient` or
   `APIs`, it's required to generate an access token.

Tokens have to be generated from the `DataHub` (Onezone) interface.

.. figure:: _static/datahub-space-token.png
   :alt: EGI DataHub token management

   Managing acccess tokens from EGI DataHub

   The access tokens can be created and managed using the EGI DataHub web interface.

Testing Oneclient in a Virtual Machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following variables have to be exported:

* `ONECLIENT_ACCESS_TOKEN`: access token allowing to access **all** the spaces.
* `ONECLIENT_PROVIDER_HOST`: name or IP of the Oneprovider the client should connect to.

.. code-block:: console

   curl -sS http://get.onedata.org/oneclient.sh | bash
   export ONECLIENT_ACCESS_TOKEN=<ACCESS_TOKEN_FROM>
   export ONECLIENT_PROVIDER_HOST=plg-cyfronet-01.datahub.egi.eu
   mkdir /tmp/space
   oneclient /tmp/space

Testing Oneclient in a Vagrant box
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It's possible to quickly test Oneclient using `Vagrant <https://www.vagrantup.com/>`_.

The following variables have to be exported:

* `ONECLIENT_ACCESS_TOKEN`: access token allowing to access **all** the spaces.
* `ONECLIENT_PROVIDER_HOST`: name or IP of the Oneprovider the client should connect to.

.. code-block:: console

   vagrant init ubuntu/xenial64
   vagrant up
   vagrant ssh
   curl -sS http://get.onedata.org/oneclient.sh | bash
   export ONECLIENT_ACCESS_TOKEN=<ACCESS_TOKEN_FROM>
   export ONECLIENT_PROVIDER_HOST=plg-cyfronet-01.datahub.egi.eu
   mkdir /tmp/space
   oneclient /tmp/space
