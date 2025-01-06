Sim Examples
============

The **sim** examples are designed to work on the simulator. The examples are located in the `ras_sim_lab` directory under the `apps` folder.

To get started with the sim examples, follow the steps below:

1. After the installation of RAS, initialize the **sim** application by running the following command:

.. code-block:: bash

    rdi sim init

.. image:: ../_static/assets/rdi_sim_init.png
    :alt: RDI Sim Init
    :align: center

`rdi sim init` will first pull application specific repositories which are defined in the *repos/apps/ras_sim_lab.repos*, then pull it's dependencies, and after that, pull docker image for the **sim** application.

2. Build the ros2 packages for the **sim** application by running the following command:

.. code-block:: bash

    rdi sim build

.. image:: ../_static/assets/rdi_sim_build.png
    :alt: RDI Sim Build
    :align: center

The above command will build the ros2 packages for the **sim** application in *apps/ras_sim_lab/ros2_ws* directory.

If you need build the docker image, then use `--force` argument with command:

.. code-block:: bash

    rdi sim build --force


3. Start the **sim** app by running the following command:

.. code-block:: bash

    rdi sim run

.. image:: ../_static/assets/rdi_sim_run.png
    :alt: RDI Sim Run
    :align: center

It will start the Gazebo simulator, Rviz2, and other necessary components for the application to work out-of-the-box. You can now interact with robot.

.. image:: ../_static/assets/ignition_rviz.png
    :alt: Ignition Rviz
    :align: center


4. To start the experiment, open the following URL in your browser:


    `localhost:5173 <http://localhost:5173>`_

The experiment files are located in the *configs/experiments* directory under `ras_sim_lab` directory, which can be used to perform different experiments.
For example, the `1.yaml` file contains the experiment details for the robot arm to perform a motion *pick and place* in the simulation.

.. code-block:: yaml
    Poses:
        out1: {x: 0.2, y: 0, z: 0.5, roll: 3.14, pitch: 0, yaw: 0}
        above1: {x: 0.2, y: -0.35, z: 0.33, roll: 3.14, pitch: 0, yaw: -1.575}
        in1: {x: 0.2, y: -0.35, z: 0.25, roll: 3.14, pitch: 0, yaw: -1.575}
        out2: {x: 0.2, y: 0, z: 0.5, roll: 3.14, pitch: 0, yaw: -1.575}
        above2: {x: 0.40, y: 0.0, z: 0.37, roll: 3.14, pitch: 0, yaw: -1.575}
        in2: {x: 0.40, y: 0.0, z: 0.33, roll: 3.14, pitch: 0, yaw: -1.575}
        out3: {x: 0.2, y: -0.12, z: 0.33, roll: 0, pitch: 1.57, yaw: 0}
        front3: {x: 0.16, y: -0.14, z: 0.16, roll: 0, pitch: 1.57, yaw: 0}
        in3: {x: 0.28, y: -0.14, z: 0.16, roll: 0, pitch: 1.57, yaw: 0}
        up4: {x: 0.28, y: -0.14, z: 0.27, roll: 0, pitch: 1.57, yaw: 0}
        left4: {x: 0.28, y: -0.06, z: 0.28, roll: 0, pitch: 1.57, yaw: 0}
        above5: {x: 0.28, y: -0.11, z: 0.45, roll: 0, pitch: 1.57, yaw: 0}
        out5: {x: 0.0, y: 0.4, z: 0.3, roll: 0, pitch: 1.57, yaw: 0}

    targets:
    - move2pose: out1
    - move2pose: above1
    - move2pose: in1
    - gripper: true
    - move2pose: above1
    - move2pose: out2
    - move2pose: above2
    - move2pose: in2
    - gripper: false
    - move2pose: above2
    - move2pose: out2
    - move2pose: out3
    - move2pose: front3
    - move2pose: in3
    - gripper: true
    - move2pose: up4
    - move2pose: left4
    - rotate: -1.57
    - rotate: 1.57
    - move2pose: above5
    - move2pose: out5
    - gripper: false

Remember the name of the file is the **Experiment ID**. Now, to run this experiment, enter *1* in the **Experiment ID** field and click **LOAD EXPERIMENT**. After that click **START SIMULATION** to start the experiment.

.. image:: ../_static/assets/rdi_experiment_browser.png
    :alt: RDI Experiment Browser
    :align: center

The robot arm will perform the motion in the simulation and trajectory will be displayed in the rviz.

Similarly, you can run other experiments which are predefined in the *configs/experiments* directory.
If you want to create your own experiment then follow the instructions in the `Real Examples <examples/real_example>`_ section.