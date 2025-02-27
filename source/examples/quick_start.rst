Quick Start
===========

This is the quick start example to get started with the RAS. RAS is an open source platform, which provides tools and functionality to control the robot. To quickly start with the experiment, you can follow this guide.

1. After the installation of RAS, initialize the **server** application by running the following command:

.. code-block:: bash

    ras server init

.. image:: ../_static/assets/rdi_sim_init.png
    :alt: ras server Init
    :align: center

`ras server init` will first pull application specific repositories which are defined in the *repos/apps/ras_server_lab.repos*, then pull it's dependencies, and after that, pull docker image for the **server** application.

.. note::

    -i argument is defined to pull the latest docker image and doesn't require if you want to use the existing docker image.

.. code-block:: bash

    ras server build

.. image:: ../_static/assets/rdi_sim_build.png
    :alt: ras server Build
    :align: center

The above command will build the ros2 packages for the **server** application in *apps/ras_server_lab/ros2_ws* directory.

(Optional) If you need build the docker image, then use `--force` argument with command:

3. Start the **server** app by running the following command:

.. code-block:: bash

    ras server run

.. image:: ../_static/assets/rdi_sim_run.png
    :alt: ras server Run
    :align: center

It will start the Gazebo Sim with XArm Robot, Rviz2, and other necessary components for the application to work out-of-the-box. You can now interact with robot.

.. image:: ../_static/assets/ignition_rviz.png
    :alt: Rviz
    :align: center

4. To start the experiment, open the terminal and go to the debugging panel. Now run the following commands:

.. code-block:: bash

    ras_cli -h

5. First, we need to load the specific experiment to run. These experiment files are defined in the config/experiments directory under `ras_sim_lab`. You can select any experiment to run from the provided. For this example, we use the experiment *0*:

.. code-block:: bash

    ras_cli load_experiment 0

This will load the experiment file *0*.

6. Next step is to start the experiment. For that run the following command:

.. code-block:: bash

    ras_cli run_sim

This will start the simulation, and you can see the robot arm performing the motion *pick and place* in the simulation.
You should wait for the experiment to complete and then continue with the next steps.

.. note::
    Based on the experiment file, the behavior tree is generated to perform the actions defined in the YAML file. Then the robot arm will perform the motion in the simulation.
    Let's consider these target actions:

    .. code-block:: yaml

        Poses:
            out1: {x: 0.2, y: 0, z: 0.5, roll: 3.14, pitch: 0, yaw: 0}
            above1: {x: 0.2, y: -0.35, z: 0.33, roll: 3.14, pitch: 0, yaw: -1.575}
            in1: {x: 0.2, y: -0.35, z: 0.25, roll: 3.14, pitch: 0, yaw: -1.575}
            out2: {x: 0.2, y: 0, z: 0.5, roll: 3.14, pitch: 0, yaw: -1.575}
            above2: {x: 0.40, y: 0.0, z: 0.37, roll: 3.14, pitch: 0, yaw: -1.575}
            in2: {x: 0.40, y: 0.0, z: 0.33, roll: 3.14, pitch: 0, yaw: -1.575}


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

    First, the XArm robot will move to the *out1* pose, which is defined as x position of gripper of robot arm is 0.2 m w.r.t. base of the robot and z is 0.5 m and roll of gripper will be 3.14, then to the *above1* pose, where the robot moves to y -0.35 m and z 0.33 m, and then to the *in1* pose, where gripper reaches z 0.25. After that, the gripper will be closed. Then the robot will move to the *above1* pose based on the pose, then to the *out2* pose, then to the *above2* pose, and then to the *in2* pose. Finally, the gripper will be opened.

7. After the experiment is completed, now this is the time to run the experiment in the robot. For that, you need to install and build the robot app with the RAS. For this quick start, we will use robot simulation using another Gazebo Sim with robot arm. Now the run following command to start the robot simulation:

.. code-block:: bash

    ras robot init

This will pull application specific repositories which are defined in the *repos/apps/ras_robot_lab.repos*, then pull it's dependencies, and after that, pull docker image for the **robot** application.

.. note::

    -i argument is defined to pull the latest docker image and doesn't require if you want to use the existing docker image.


8. Build the ros2 packages for the **robot** application by running the following command:

.. code-block:: bash

    ras robot build

The above command will build the ros2 packages for the **robot** application in *apps/ras_robot_lab/ros2_ws* directory.


(Optional) If you need to build the docker image, then use `--force` argument with command:

.. code-block:: bash

    ras robot build --force


9. Start the **robot** app by running the following command:

.. code-block:: bash

    ras robot run sim

It will start the Gazebo Sim with XArm Robot, Rviz2, and other necessary components for the application to work out-of-the-box. You can now also interact with robot.

10. To start the experiment, use the same terminal described in step 4. Now run the following commands:

.. code-block:: bash

    ras_cli run_real

This will send the behavior tree generated by sim app to robot app, and robot app will perform the trajectory. You can now see the robot arm performing same motion *pick and place* in the robot simulation. Also, the robot and simulation robot are synchronized to perform the same motion.


This is all for the quick start guide. You can now explore more features and functionalities of RAS by going through the documentation.

Run the experiment using ros2 cli for developers
------------------------------------------------

You can also run the experiment using the ros2 cli. For that, you need to follow the following steps:

1. In order to load the experiment, run the following command:

.. code-block:: bash

     ros2 service call /get_exepriment ras_interfaces/srv/LoadExp "{exepriment_id: 0, instruction_no: '', picked_object: ''}"

This will load the experiment file *0*.

2. Next step is to start the experiment. For that run the following command:

.. code-block:: bash

    ros2 service call /test_experiment std_srvs/srv/SetBool "data: false"

This will start the simulation, and you can see the robot arm performing the motion *pick and place* in the simulation.

3. After the experiment is completed, now this is the time to run the experiment in the real robot. For that, you need to connect the real robot with the RAS. But for this quick start we will simulate another Gazebo Sim with robot arm to pretend it as real robot. Now the run following command to start the real robot simulation:

.. code-block:: bash

    ros2 action send_goal /execute_exp ras_interfaces/action/ExecuteExp {}

This will send the behavior tree generated by sim app to real app, and real app will perform the trajectory. You can now see the robot arm performing same motion *pick and place* in the real simulation. Also, the real and simulation robot are synchronized to perform the same motion.
