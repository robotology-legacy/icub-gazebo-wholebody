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

 ```
 When the world is created the two robots are spawned along with the board on top of their hands. The board and the hands of the robots are not linked at this state, but the `board` model is created with the [linkattacher](https://github.com/robotology/gazebo-yarp-plugins/tree/master/plugins/linkattacher) gazebo-yarp-plugin which is be used to attach the robots hands and the board. The bash script `handlesHandsLinkAttacher.sh` inside the `board` model directory will achieve this. The usage is as following:

```
./handlesHandsLinkAttacher.sh attach -----> Attach the handle links of the board to the hand links of the two robot
./handlesHandsLinkAttacher.sh detach -----> Detach the handle links of the board from the hand links of the two robot
 ```

 **NOTE:** If the bash script is throwing error there may be a possible naming issue of the icub models spawned in gazebo. The default names of the two iCub robots assumed for this bash script are `iCub1` and `iCub2`.


