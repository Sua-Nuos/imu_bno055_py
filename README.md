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
  - 3. sudo i2cdetect -y 5 you will see addr:28
  - 4. pip3 install adafruit-circuitpython-bno055
  - 5. add I2C ports in file: ~/.local/lib/python3.10/site-packages/adafruit_blinka/microcontroller/bcm2711/pin.py
       ```
       i2cPorts = (
        (1, SCL, SDA),
        (0, D1, D0),  # both pi 1 and pi 2 i2c ports!
        (10, D45, D44),  # internal i2c bus for the CM4
        (5, D11, D10) # <<< add this line
       )
       ```
    


## 1.Calibrate: 
run this file -> /Adafruit_CircuitPython_BNO055/examples/bno055_calibrator.py

## 2. insert offset to bno055_params_i2c.yaml [https://www.simonv.fr/TypesConvert/?integers]

## 3. RUN NODE: 
  ### 3.1 cd name_ws
  ### 3.2 
  ```
  ros2 run bno055 bno055 --ros-args --params-file ./src/bno055/bno055/params/bno055_params_i2c.yaml
  ```
