# About
Open-source modules for ICRA 2019 submission "Learned Map Prediction for Enhanced Mobile Robot Exploration"

# Supplementary Video
[![Learned Map Prediction for Enhanced Mobile Robot Exploration
](https://img.youtube.com/vi/NRgXYdxroJE/0.jpg)](https://youtu.be/NRgXYdxroJE "Supplementary Video")

# Preprint
[Link](https://github.com/rakeshshrestha31/map_prediction_enhanced_exploration/blob/master/shrestha_icra19_preprint.pdf)

# Modules
## Online Map Completion
Variational Autoencoder Network for map prediction

## online_map_completion_msgs
ROS messages and services for communicating the map prediction data

## Stage frontier datagen
Data generation and exploration evaluation programs

## Ground truth layer
ROS Costmap layer for building ground truth maps from laser and pose

## Stage
Fork of Stage Simulator [rtvstage](https://github.com/rtv/Stage)

## Hector navigation
Fork of hector navigation for hector exploration planner ([hector_navigation](https://github.com/tu-darmstadt-ros-pkg/hector_navigation))

## libfloorplan
Fork of [kth_libfloorplan](https://github.com/alperv/libfloorplan) for parsing KTH floorplan dataset

# Building

## Clone the repo to src directory of your workspace
```
git clone https://github.com/rakeshshrestha31/map_prediction_enhanced_exploration
cd map_prediction_enhanced_exploration
git submodule update --init --recursive
```

## install dependencies
```
bash install_deps.sh
rosdep install --from-paths src --ignore-src -y -r
```

## Build the Stage simulator
```
cd <stage_directory>
mkdir build
cd build
cmake ..
make -j<num_jobs>
sudo make install
```
(Note: if you don't want the simulator to be installed in /usr/local set CMAKE\_INSTALL\_PREFIX appropriately)

## Build the libfloorplan library
```
cd <libfloorplan_directory>
mkdir build
cd build
cmake ..
make -j<num_jobs>
make install
# this can be added to .bashrc or .zshrc
export LIB_FLOORPLAN_PATH=<libfloorplan_directory>
```

## Build the catkin workspace
```
catkin build
```

## Download KTH dataset
```
cd <datasets_directory>
wget http://www.csc.kth.se/~aydemir/KTH_CampusValhallavagen_Floorplan_Dataset.tar.bz2
tar xvf KTH_CampusValhallavagen_Floorplan_Dataset.tar.bz2
```

## Generating partial maps dataset
```
rosrun stage_frontier_datagen kth_stage_node _dataset_dir:=<kth_dataset_dir> _data_record_dir:=<generated_dataset_dir>
```
