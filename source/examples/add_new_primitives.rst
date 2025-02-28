How to add new primitives
==========================

The RAS provides an easier way to add new primitives to the existing primitives. For that, you need to follow the below steps:

1. Open the file *ros2_ws/src/ras_bt_framework/config/primitive_declaration.yaml* and add the new primitive to the existing primitives list as shown below:

.. code-block:: yaml

    primitives:
        primitive_name:
            type: primitive_type
          input_ports:
              name: type
          output_ports:
              name: type

    # Example

    primitives:
      move2joints:
        type: trajectory
        input_ports: 
          joints: b
        output_ports: 
          status: bool

2. Now, run the command

.. code-block:: bash

    ros2 run ras_bt_framework generate_primitives.py

    # output

This will generate the new primitive file in the *ros2_ws/src/ras_bt_framework/generated_files* directory.

3. Now, you can use the new primitive template and modify the primitive as per your required behavior.

4. Once you are done with the modification, you can run the command
