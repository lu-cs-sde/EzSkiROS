# EzSkiROS for People in a Hurry (Docker container)

![Docker Image Version (latest by date)](https://img.shields.io/docker/v/rdinizcal/ezskiros?label=docker%20&style=plastic)

This section guides you how to get EzSkiROS running in your environment in less than 5 minutes. In the container you can:
 - [run simulations](#run-simulations) of robots and replicate our experiments to catch bugs early
 - read, write, and run [automated tests](#run-automated-tests) for skill descriptions
 - [inspect EzSkiROS's code](#inspect-the-code) to understand how we implemented the robotic patterns in practice

## Requirements

- ```ezskiros-demo``` is a pre-built image supporting the **linux/x86** architecture
- Install [Docker](https://www.docker.com/)

## Loading the Docker image

First, pull the docker image to create the container:
```
docker pull rdinizcal/ezskiros:demo
```

Then, run the container using the command:
```
sudo docker run -v /dev/dri:/dev/dri -v /tmp/.X11-unix:/tmp/.X11-unix -e TERM -e DISPLAY --ipc=host --net=host -v $XAUTHORITY:$XAUTHORITY -e XAUTHORITY -v "$(readlink -f ./shared):/shared" --name ezskiros -it rdinizcal/ezskiros:demo
```

If the image is running correctly, your terminal should look like ```ezskiros@[workplace]``` indicating that you are inside the docker image.

## Environment setup

### ROS setup
 
Assuming that your shell is `bash`, run:
```
source /opt/ros/noetic/setup.bash
```

### Catkin workspace setup

Catkin workspace has already set up. Go to the ```catkin_ws```:
```
cd home/ezskiros/catkin_ws/
```

To set up the environment, run:
```source devel/setup.bash```

## Run Simulations

Assuming that the [Environment setup](#environment-setup) was carried out.

Run ```roscore &``` and press enter

Then, run ```mon launch heron_launch simulation.launch ```

A simulation of Heron, our robot, should appear on your screen with the SkiROS GUI loading all the skills. You can run ```mir_drive``` skill (a skill written in EzSkiROS) by setting the goal location on the right hand side of the GUI. 

## Run Automated Tests

To run unit tests with EzSkiROS, you can run the script:
```catkin test ezskiros skills_sandbox```
and all tests should pass.

## Inspect the Code

To check early bug detection, you can introduce a wrong relation for ```hasA``` in the ```home/ezskiros/catkin_ws/src/skills/skills_sandbox/arm_motion/pick_place_descriptions``` and then launch the simulation as described above and you can observe a TypeError at launch time.

### Contributors

Momina Rizwan<sup>1</sup>, [Ricardo Caldas](https://rdinizcal.github.io)<sup>2</sup>, Christoph Reichenbach<sup>1</sup>, Matthias Mayr<sup>1</sup>  

<sup>1</sup> Department of Computer Science, Faculty of Engineering (LTH), Lund University <br>
<sup>2</sup> Department of Computer Science and Engineering, Chalmers University of Technology
