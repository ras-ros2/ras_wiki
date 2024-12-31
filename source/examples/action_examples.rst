Action Examples
===============

This example demonstrates how to create a simple action and use it with the RAS.

The actions can be defined in the **config\experiments** folder inside the `ras_sim_lab` where you can create a .yaml file which can be used to define the actions for the robot to perform.

Example 1
---------

1. Create a new yaml file e.g. 5.yaml in the **config\experiments** folder inside the `ras_sim_lab`.

2. First define the poses for the robot. The poses are defined as a dictionary with the keys as the name of the pose and the values as the pose values. The pose values are defined as a dictionary with the keys as the x, y, z, roll, pitch and yaw values. See the example below and create a similar dictionary for the poses.:

.. code-block:: yaml

    Poses:
        out1: {x: 0.2, y: 0, z: 0.5, roll: 3.14, pitch: 0, yaw: 0}


3. Next define the targets for the robot. The targets are defined as a list of actions that the robot should perform.

Currently the following actions are supported:

    - The **move2pose** action is used to move the robot to a specific pose. The value of the action is the name of the pose that the robot should move to.

    - The **gripper** action is used to open or close the gripper. The value of the action is a boolean value where `true` means the gripper should be closed and `false` means the gripper should be opened.

    - The **rotate** action is used to rotate the end-effector. The value of the action is the angle in radians that the robot should rotate.

The actions are defined as a dictionary with the keys as the action name and the values as the action values. See the example below:

.. code-block:: yaml

    targets:
        - move2pose: out1
        - gripper: true

4. Here is the complete yaml file for the example:

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


5. Start the **sim** application by running the following command:

.. code-block:: bash

    rdi sim dev

    ras_app

6. To start the experiment, open the following URL in your browser:

    `localhost:5173 <http://localhost:5173>`_

Then enter *5* in the **Experiment ID** field and click **LOAD EXPERIMENT**. After that click **START SIMULATION** to start the experiment.

7. This will start the robot and it will perform the actions defined in the yaml file.


Example 2
---------

Example 3
---------