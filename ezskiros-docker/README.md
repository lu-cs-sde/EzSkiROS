# EzSkiROS Docker container

This repository documents an embedded Domain-specific language (DSL) to describe robotic skills in SkiROS. It allows robot developers to catch bugs in the SkillDescription at launch time (before running the robot).

## Supported architectures

The ```ezskiros-demo``` pre-built image supports **linux/x86** architecture.

## Loading the Docker image

First, load the docker image to create the container
```
docker load < ezskiros-demo.tar.gz
```

then run the container using the command ```./run-demo.sh```. 

##  In the Docker image: set up ROS  
   Assuming that your shell is `bash`: within the Docker image, run
```
source /opt/ros/noetic/setup.bash
```

### Catkin workspace
Catkin workspace has already set up. Go to the ```catkin_ws```:

```
cd home/ezskiros/catkin_ws/
```
To set up the environment, run:

```source devel/setup.bash```

## Integration test : Running SkiROS (Validation

Run:
```roscore &``` and press enter
Then run:
```mon launch heron_launch simulation.launch ```

### Contributors

Momina Rizwan<sup>1</sup>, Ricardo Caldas<sup>2</sup>, Christoph Reichenbach<sup>1</sup>, Matthias Mayr<sup>1</sup>  

<sup>1</sup> Department of Computer Science, Faculty of Engineering (LTH), Lund University <br>
<sup>2</sup> Department of Computer Science and Engineering, Chalmers University of Technology
