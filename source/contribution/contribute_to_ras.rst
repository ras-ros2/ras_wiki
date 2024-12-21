How to contribute to the RAS
============================

To contribute to the RAS, follow the steps below:

1. Fork the repository which you want to contribute to.

2. After that you can replace the `deps.repos` file to your own repos.

3. Then run the following command:

.. code-block:: bash

    rdi sim init

    rdi sim build

This will clone the repositories to your local machine and build the packages. Now you can make changes to the repositories, test the packages and contribute to the RAS.

How to use docker extension for the RAS
=======================================

For easier development, you can use the docker extension for the RAS. To use the docker extension, follow the steps below:

1. Install the docker extension in the VSCode.

2. Then run start the container by running the following command:

.. code-block:: bash

    rdi sim dev

3. After that you can open the VSCode and connect to the container by clicking on the `Remote Explorer` icon.