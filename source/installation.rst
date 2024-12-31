Installation
============

RAS Docker is the main workspace where two applications, **sim** and **real**, can be worked with seamlessly. This document provides an overview of its setup and usage.

Steps to install RAS
--------------------

1. Clone the Repository

.. code-block:: bash

    git clone --recursive https://github.com/ras-ros2/ras_docker

RAS Docker Interface (RDI)

RAS Docker includes a command-line utility called **RDI** (RAS Docker Interface), implemented in ``docker_interface.py`` under the ``scripts`` directory.

2. Source the Environment File

.. code-block:: bash

    source ./ras_docker/env.sh

3. Check Available Commands

.. code-block:: bash

    rdi -h

To see the available RDI commands

Directory Structure
-------------------

`apps` Directory
~~~~~~~~~~~~~~~~
The `apps` directory houses the two applications, **sim** and **real**, which are Docker containers built using the Docker images located in the `context` directory.

`context` Directory
~~~~~~~~~~~~~~~~~~~
The `context` directory contains the Docker images used to build the applications:

1. **Dockerfile.base**: Based on the `humble-desktop-full` image, it installs dependencies common to both applications (e.g., `python3-pip`).

2. **Dockerfile.sim**: Extends `Dockerfile.base` and adds dependencies specific to the **sim** application (e.g., `ignition-fortress`).

3. **Dockerfile.real**: Extends `Dockerfile.base` and adds dependencies specific to the **real** application.

4. Check App-Specific Commands

.. code-block:: bash

    rdi sim -h

To see commands specific to an application (e.g., `sim`)