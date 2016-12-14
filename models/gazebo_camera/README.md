# How to use the gazebo camera

## Requirements
You need to install `ffmpeg` on your computer. This can be done easlily in Ubuntu with the following command on terminal:

	sudo apt-get install ffmpeg
	
## Installation
The path to the folder where your pictures will be saved is, by default, `/home/username/gazebo_camera`. A folder named `gazebo_camera` will be 
automatically generated in your home directory. If you want to modify it, change the path in the `gazebo_camera.sdf` file.

## Usage
- put the camera in Gazebo simulator, in front of the object you want to record;
- run your simulation;
- stop the simulation and `remove the camera`;
- open a terminal and run: 

	 `ffmpeg -framerate 30 -start_number 0 -i default_camera_0_link_camera\(1\)\-%04d.jpg -s 1280x960 your_video.mp4`

You may need to change the name of the images according to the name of the files inside the `gazebo_camera` folder.
