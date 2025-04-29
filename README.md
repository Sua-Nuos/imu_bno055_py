# imu_bno055_py
## 0.config:
  - 1.
      ```
      sudo nano /boot/firmware/config.txt
      ```
  - 2. 
```
dtparam=audio=on
dtparam=i2c_arm=on
dtparam-i2c_arm_baurate=400000
dtparam=spi=off

dtoverlay=i2c5,pins_10_11
dtoverlay=i2c6
dtoverlay=i2c-fan,i2c6,emc2301
```


## 1.Calibrate: 
run this file -> /Adafruit_CircuitPython_BNO055/examples/bno055_calibrator.py
## 2. RUN NODE: 
  ### 2.1 cd name_ws
  ### 2.2 ros2 run bno055 bno055 --ros-args --params-file ./src/bno055/bno055/params/bno055_params_i2c.yaml
