## To load iCub standup world in Gazebo

Normally, for loading a `world`, Gazebo needs to be launched in the folder where the `world` is. You can avoid this by appending these lines to your `.bashrc`:

```
source /usr/share/gazebo/setup.sh
export GAZEBO_RESOURCE_PATH=$GAZEBO_RESOURCE_PATH:/PATH/TO/WORLD/FOLDER

```

Furthermore, if you are working with Simulink controllers, it is necessary to sincronize Gazebo with Simulink by running Gazebo with the option `-slibgazebo_yarp_clock.so`. 

Final command to run in the terminal is something like this: `gazebo -slibgazebo_yarp_clock.so worldFolderName/nameOfYourWorld` where for iCub standup demo `worldFolderName/nameOfYourWorld = icub_standup_world/icub_standup.world`.


