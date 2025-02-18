## FishEye-Calib-Tools 鱼眼相机标定工具

## 环境准备
- ROS1 Noetic
- Ceres 2.1.0
- OpenCV 4

```bash
sudo apt install libdw-dev
```

## 编译
```bash
mkdir -p ws_fisheye_calib_tools/src
cd ws_fisheye_calib_tools/src
git clone https://github.com/Derkai52/FishEye-Calib-Tools.git
cd .. && catkin_make
```

## 使用

```bash
# 采集标定数据
roslaunch calib_image_saver single_collect_image.launch


# 标定
rosrun camera_model Calibration --camera-name mycamera --input /home/tk/robust_vins/src/calib_image_saver/calibrationdata -w 8 -h 6 --size 70 --camera-model myfisheye --opencv true

# 实时畸变矫正
roslaunch fisheye_flattener flattener.launch
```

## 引用参考
- https://github.com/gaowenliang/calib_image_saver.git

- https://github.com/gaowenliang/camera_model.git

- https://github.com/alexacw/fishEyeFlattener.git