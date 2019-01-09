## To load a gazebo world with two icubs comanipulating a board

Normally, for loading a `world`, Gazebo needs to be launched in the folder where the `world` is. You can avoid this by appending these lines to your `.bashrc`:

```
source /usr/share/gazebo/setup.sh
export GAZEBO_RESOURCE_PATH=$GAZEBO_RESOURCE_PATH:/PATH/WHERE/YOUR/WORLD/IS

```

Furthermore, if you are working with Simulink controllers, it is necessary to synchronize Gazebo with Simulink by running Gazebo with the option `-slibgazebo_yarp_clock.so`.

Final command to run in the terminal is something like this: `gazebo -slibgazebo_yarp_clock.so nameOfYourWorld`. For seesaw demo, it is also required to start Gazebo in "pause" mode, and therefore final command will be: `gazebo -slibgazebo_yarp_clock.so two_icubs_comanipulation -u`.

Alternatively you can add an alias to your `.bashrc` which will let you run a smaller command from the terminal to launch gazebo with this world. As an example add the following line to your `.bashrc`
`alias gazebo_prri="gazebo -slibgazebo_yarp_clock.so two_icubs_comanipulation -u --verbose"`

The option `--verbose` enables verbose output on the terminal running gazebo

For **two_icubs_comanipulation** it is also necessary to avoid using the standard `gazeboYarpPluginsRobotName` for the two robots, otherwise the two models would share the name `icubSim` and the control boards of one of the two model fail.
This can be done by editing [gazebo_icub_robotname.ini](https://github.com/robotology/icub-gazebo/blob/master/icub/conf/gazebo_icub_robotname.ini) file, and commenting out the following line:
 ```
 gazeboYarpPluginsRobotName icubSim
