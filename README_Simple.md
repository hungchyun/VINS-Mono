1. Install ROS dependencies.  
$ sudo apt-get install ros-melodic-cv-bridge ros-melodic-tf ros-melodic-message-filters ros-melodic-image-transport  

2. Install Ceres solver, install guide http://ceres-solver.org/installation.html.  
2.1 Download the latest stable version from http://ceres-solver.org/ceres-solver-2.0.0.tar.gz
$ sudo apt-get install cmake  
$ sudo apt-get install libgoogle-glog-dev libgflags-dev  
$ sudo apt-get install libatlas-base-dev  
$ sudo apt-get install libeigen3-dev  
$ sudo apt-get install libsuitesparse-dev  
2.2 Move to the directory of ceres-solver-2.0.0.tar.gz  
$ tar zxf ceres-solver-2.0.0.tar.gz  
$ mkdir ceres-bin  
$ cd ceres-bin  
$ cmake ../ceres-solver-2.0.0  
$ make -j3  
$ make test  
$ sudo make install  

3. Run EuRoC MAV dataset.  
$ roslaunch vins_estimator euroc.launch  
$ roslaunch vins_estimator vins_rviz.launch  
$ rosbag play YOUR_PATH_TO_DATASET/MH_01_easy.bag  
3.1. Ue robbag play pause to debug
$ rosbag play --pause YOUR_PATH_TO_DATASET/MH_01_easy.bag
3.2. Hit "space" key to start/stop rosbag play.  

4. Run event camera, davis 240c, dataset.  
$ roslaunch vins_estimator davis_240c.launch  
$ roslaunch vins_estimator vins_rviz.launch  
$ rosbag play YOUR_PATH_TO_DATASET/MH_01_easy.bag  
4.1. Ue robbag play pause to debug
$ rosbag play --pause YOUR_PATH_TO_DATASET/MH_01_easy.bag
4.2. Hit "space" key to start/stop rosbag play.  
4.3. VINS saves estimated trajectory via .csv format. Modify the directory of .csv files by the parameter, output_path, in /VINS-Mono/config/${DATASET}/${YOUR_CONFIG}.yaml.  