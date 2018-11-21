## To load two icubs standup world in Gazebo

Normally, for loading a `world`, Gazebo needs to be launched in the folder where the `world` is. You can avoid this by appending these lines to your `.bashrc`:

```
source /usr/share/gazebo/setup.sh
export GAZEBO_RESOURCE_PATH=$GAZEBO_RESOURCE_PATH:/PATH/WHERE/YOUR/WORLD/IS
```

Furthermore, if you are working with Simulink controllers, it is necessary to sincronize Gazebo with Simulink by running Gazebo with the option `-slibgazebo_yarp_clock.so`. 

Final command to run in the terminal is something like this: `gazebo -slibgazebo_yarp_clock.so nameOfYourWorld`.

For **two_icubs_standup** it is also necessary to avoid using the standard `gazeboYarpPluginsRobotName` for the two robots, otherwise the two models would share the name `icubSim` and the control boards of one of the two model fail.
This can be done by editing [gazebo_icub_robotname.ini](https://github.com/robotology/icub-gazebo/blob/master/icub/conf/gazebo_icub_robotname.ini) file, and commenting out the following line:
 ```
 gazeboYarpPluginsRobotName icubSim
 ```

 When the world is created the two robots are not linked, but the model `iCub` is created with the [`linkattacher`](https://github.com/robotology/gazebo-yarp-plugins/tree/master/plugins/linkattacher) plugin that can be used to attach the robots hands:
 ```
 $ yarp rpc /iCub/linkattacher/rpc:i
> attachUnscoped iCub l_hand iCub_0 r_hand
> attachUnscoped iCub r_hand iCub_0 l_hand
 ```