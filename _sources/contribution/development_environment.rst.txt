How to setup runtime development environment
============================================

This guide outlines steps for setting up the runtime development environment for RAS.


1. After the installation of RAS, initialize the **sim** application by running the following command:
-------------------------------------------------------------------------------------------------------
.. code-block:: bash

    rdi sim init

.. image:: ../_static/assets/rdi_sim_init.png
    :alt: RDI Sim Init
    :align: center

2. Build the Docker image for the **sim** application by running the following command:
--------------------------------------------------------------------------------------------
.. code-block:: bash

    rdi sim build

.. image:: ../_static/assets/rdi_sim_build.png
    :alt: RDI Sim Build
    :align: center

3. Start the **dev environment** by running the following command:
------------------------------------------------------------------
.. code-block:: bash

    rdi sim dev

Using this command, the bash of the container will be opened. You can now interact with the container.