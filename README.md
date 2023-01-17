# Husky-Robot-Setting  

## Environemnt  
- Hardware  

||Spec|  
|:---:|:---:|  
|mini PC|intel NUC| 
|CPU|Intel® Core™ i7-10710U| 
|GPU|GTX 1660 Ti| 
|LiDAR|Velodyne VLP 16|
|Camera|ZED 2i|
|IMU|Xsens Mti 100| 

- Software  

||Version|  
|:---:|:---:|  
|ROS|Melodic|  
|Ubuntu|18.04|    
|CUDA|11.7|  
|ZED SDK|3.8.2|



## Requirement  

### 1. GPU model check  
```
sudo update-pciids
```
```
lspci -k | grep VGA
```


### 2. [Husky Robot environment](https://www.clearpathrobotics.com/assets/guides/kinetic/ros/Drive%20a%20Husky.html)  
```
sudo apt-get update && \
sudo apt-get install ros-melodic-husky-desktop && \
sudo apt-get install ros-melodic-husky-simulator
```  

Create an udev rule for Husky connetion. - [reference](https://github.com/psh117/husky_kinetic_custom_installation)  
```
sudo vi /etc/udev/rules.d/90-clearpath.rules
```
```
# Udev rule for the Prolific Serial-to-USB adapter shipped standard with Husky
SUBSYSTEMS=="usb", ATTRS{manufacturer}=="Prolific*", SYMLINK+="prolific prolific_$attr{devpath}", MODE="0666"
```
```
sudo udevadm control --reload-rules && sudo service udev restart && sudo udevadm trigger
```

### 3. [Velodyne ROS](https://wiki.ros.org/velodyne)  
```
sudo apt-get install ros-melodic-velodyne
```

### 4. XBox bluetooth controller  
1. Connect XBox controller to Ubuntu - [reference](https://youtu.be/ld_elDk2Nxs)  
2. Install xbox ubuntu drive  
```
sudo apt-add-repository -y ppa:rael-gc/ubuntu-xboxdrv && \
sudo apt-get update && \
sudo apt-get install ubuntu-xboxdrv
```


