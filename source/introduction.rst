.. toctree::

Introduction
------------

Motivation
``````````

* Putting up a (scalable) distributed data infrastructure needs specific expertise, resources and knowledge
* No easy way to discover and transfer data
* No easy way of making data (publicly) accessible without transferring it a sharing service
* No easy way of combining multiple datasets from different data providers
* Users need to access data locally and from compute resources

Components and concepts
```````````````````````

:Space: a virtual volume where users will organize their data. A space is
        supported by one or multiple Oneproviders providing actual storage
        resources

:EGI DataHub: a Onedata Onezone, the federation and authentication service. Single
              Sign On (SSO) with all the connected storage providers (Oneprovider)
              through EGI Check-in

:Onezone: a central component federating providers, it will take care of
          Authentication and Authorization and other management tasks (like
          space creation). EGI DataHub is a Onezone instance.

:Oneprovider: a data management component deployed in the data centres,
              provisioning data and managing transfers. A Oneprovider is
              typically deployed at a site near the local storage resources,
              and can access local storage resources over multiple connectors
              (CEPH, POSIX,...). A default one is operated for EGI by CYFRONET.

:Oneclient: a client application providing access to the spaces through a FUSE
            mount point (local POSIX access). Spaces are accessible as if they
            were part of the local file system. Oneclient can be used from VM,
            containers, desktop,...

            Web interfaces and APIs are also available

Highlighted features
````````````````````

.. figure:: _static/datahub-space-web.png
   :alt: EGI DataHub space web view

   Viewing a data space using the EGI DataHub web interface

   Using the EGI DataHub web interface it's possible to manage the space.

.. figure:: _static/datahub-space-oneclient.png
   :alt: EGI DataHub space oneclient console view

   Viewing a data space in a console locally mounted using Oneclient

   Using Oneclient it's possible to mount a space locally, and access it over a
   POSIX interface, using files as they were storred locally. The file's blocks
   are downloaded on demand.

.. figure:: _static/datahub-replica-management.png
   :alt: EGI DataHub file replica distribution

   Viewing file distribution over the Oneproviders

   In Onedata the file distribution is dong on a block basis, blocks will be
   replicated on the fly, and it's possible to instrutmentize the replication.

.. figure:: _static/datahub-metadata-management.png
   :alt: EGI DataHub metadata management

   Management of metadata using the web interface

   Three different format of metadata can be attached to files: basic
   (key/value), JSON and RDF. The metadata can be managed using the Web
   interface and the APIs. It's also possible to create indexes and query them.

.. figure:: _static/datahub-file-popularity-smarch-caching.png
   :alt: EGI DataHub file popularity information

   Viewing file popularity for smart caching

   It's possible to view the popularity of a file and manage smart caching.
