How to setup runtime development environment
============================================

This guide outlines steps for setting up the runtime development environment for RAS.


1. After the installation of RAS, initialize the **server** application by running the following command:

.. code-block:: bash

    ras server init

.. image:: ../_static/assets/ras_server_init.png
    :alt: RDI Server Init
    :align: center

2. Build the Docker image for the **server** application by running the following command:

.. code-block:: bash

    ras server build

.. image:: ../_static/assets/ras_server_build.png
    :alt: RDI Server Build
    :align: center

3. Start the **dev environment** by running the following command:

.. code-block:: bash

    ras server dev

Using this command, the bash of the container will be opened. You can now interact with the container.

4. Ro run the **dev environment** with root privileges, run the following command:

.. code-block:: bash

    ras server dev -r

5. If you want to install additional packages in the dev container and commit the changes to the docker image, run the following command:

.. code-block:: bash

    ras server dev -c

This will start the container with root privileges and open the bash. You can now install the required packages, after that you can exit the container with `exit` command. The changes will be committed to the docker image.

Now you can push the docker image to the docker hub but if you want to restore the docker image to previous state, you can run the following command:

.. code-block:: bash

    ras server init -i


How to check which Repositories has to update
=============================================

In order to check which repositories have to update, run the following command:

.. code-block:: bash

    ras server init

This will show the list of repositories that have to update.

