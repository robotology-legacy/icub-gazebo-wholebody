# icub-gazebo-wholebody
Gazebo models and worlds for simulating scenarios related to iCub Whole Body Control.

The world and models in this repository are mantained by the [Dynamic Interaction Control Group](https://www.iit.it/research/lines/dynamic-interaction-controlicub-gazebo-wholebody) and are mostly related to whole body balancing and walking, related to the FP7 European Projects CoDyCo and Koroibot and the H2020 Project AnDy.

# Usage

## From the build tree

If `<icub-gazebo-wholebody>` is the folder where this repository has been cloned, and the model you want to use is `iCubGenova04`, execute:

```
cd <icub-gazebo-wholebody>
mkdir build
cd build
cmake -DROBOT_NAME=iCubGenova04 ..
```

After this, append `<icub-gazebo-wholebody>/build/gazebo/models` to the `GAZEBO_MODEL_PATH` enviromental variable.

## From the install tree

This project can be installed executing also:

```
cmake .. \
      -DCMAKE_INSTALL_PREFIX=<prefix> \
      -DROBOT_NAME=iCubGenova04
cmake --build . --target install
```

For more info see the [`icub-gazebo`](https://github.com/robotology/icub-gazebo) and [`icub-models`](https://github.com/robotology-playground/icub-models) repositories.

# Maintainer

[Gabriele Nava](https://www.iit.it/it/people/gabriele-nava) ( [@gabrielenava](https://github.com/gabrielenava) ).
