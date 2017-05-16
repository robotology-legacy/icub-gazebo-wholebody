## To load iCub standup world in Gazebo

Normally, for loading a `world`, Gazebo needs to be launched in the folder where the `world` is. Furthermore, if you are working with Simulink controllers, it is necessary to sincronize Gazebo with Simulink using the command `gazebo -slibgazebo_yarp_clock.so`. 

For this reason, it is suggested to set an alias in your `.bashrc`:

  `alias gazebo_standup="cd YOUR/PATH/TO/THE/WORLDS/FOLDER/worlds/icub_standup_world && gazebo -slibgazebo_yarp_clock.so`

If you installed this repository using `codyco-superbuild`, the alias will be:

`alias gazebo_standup="cd $CODYCO_SUPERBUILD_ROOT/build/install/share/gazebo/worlds/icub_standup_world && gazebo -slibgazebo_yarp_clock.so`

Then, on a terminal, you can run `gazebo_standup`
