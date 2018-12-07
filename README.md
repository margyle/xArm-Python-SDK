# xArm-Python-SDK

## Overview
xArm Python SDK

## Update Summary for 0.0.11
- Support serial port and TCP connection
- Support parameter to enable reporting
- Support callback register and release
- Support Gripper setting
- Support servo setting (Some interfaces are limited to professional debugging)
- Unified return value
- Snaps an exception and returns the specified return value

## Update Summary for 0.0.12
- By specifying the value of the default parameter of the interface in the instantiation parameter, using angle or radians
- Unify all interfaces by default using angle or radians
- More interface routines
- More detailed interface documentation
- Richer interface
- Set interface alias
- Modified the default values of the default parameters of some interfaces, but support the use of parameters to be compatible when instantiating

## Caution
- There is currently no collision detection, so try not to be close during use.
- During use, people should stay away from the robot arm to avoid accidental injury or damage to other items by the robot arm.
- Protect the arm before use.
- Before you exercise, please make sure you don't encounter obstacles.
- Protect the arm before unlocking the motor.

## Installation
Install is not necessary, you can run examples without installation.
- download

  ``` git clone git@github.com:xArm-Developer/xArm-Python-SDK.git```
- install

  ``` python setup.py install ```

## Doc
- #### [API](doc/api/xarm_api.md)
- #### [API Code](doc/api/xarm_api_code.md)

## Example
- #### [xArm](example/wrapper/)

- #### Import
  ```
  from xarm.wrapper import XArmAPI
  xarm = XArmAPI('COM5')
  xarm = XArmAPI('192.168.1.185')
  xarm = XArmAPI('192.168.1.185', enable_report=False)
  xarm = XArmAPI('192.168.1.185', do_not_open=False)
  xarm = XArmAPI('192.168.1.185', report='normal')
  xarm = XArmAPI('192.168.1.185', limit_velo=[1, 1000])
  ```
- #### Connect/Disconnect
  ```
  xarm.connect(...)
  xarm.disconnect()
  ```
- #### Move
  ```
  xarm.reset(...)
  xarm.set_position(...)
  xarm.set_servo_angle(...)
  xarm.set_servo_angle_j(...)
  xarm.move_gohome(...)
- #### Set
  ```
  xarm.set_servo_attach(...)
  xarm.set_servo_detach(...)
  xarm.set_state(...)
  xarm.set_mode(...)
  xarm.motion_enable(...)
  xarm.set_sleep_time(...)
  ```
- #### Get
  ```
  xarm.get_version()
  xarm.get_state()
  xarm.get_is_moving()
  xarm.get_cmdnum()
  xarm.get_err_warn_code()
  xarm.get_position(...)
  xarm.get_servo_angle(...)
  ```
- #### Gripper
  ```
  xarm.set_gripper_enable(...)
  xarm.set_gripper_speed(...)
  xarm.set_gripper_position(...)
  xarm.get_gripper_position()
  ```
- #### Register/Release
  ```
  xarm.register_report_callback(...)
  xarm.register_report_location_callback(...)
  xarm.register_connect_changed_callback(callback)
  xarm.register_state_changed_callback(callback)
  xarm.register_maable_mtbrake_changed_callback(callback)
  xarm.register_error_warn_changed_callback(callback)
  xarm.register_cmdnum_changed_callback(callback)
  xarm.release_report_callback(callback)
  xarm.release_report_location_callback(callback)
  xarm.release_connect_changed_callback(callback)
  xarm.release_state_changed_callback(callback)
  xarm.release_maable_mtbrake_changed_callback(callback)
  xarm.release_error_warn_changed_callback(callback)
  xarm.release_cmdnum_changed_callback(callback)
  ```
- #### Property
  ```
  xarm.connected
  xarm.version
  xarm.position
  xarm.angles
  xarm.state
  xarm.error_code
  xarm.warn_code
  xarm.cmd_num
  ```

