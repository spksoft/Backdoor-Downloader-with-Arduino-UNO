# Backdoor Downloader with Arduino UNO R3
#### More infomation : [sPkBlog](http://spksoft.in.th/wordpress/?p=238)
##### Requirement list:

 * Arduino UNO R3
 * OS (We recomment linux)
 * [dfu-programmer packet](https://dfu-programmer.github.io/)
 * [Arduino-keyboard-0.3.hex (USB keyboard firmware)](http://hunt.net.nz/users/darran/weblog/b3029/Arduino_UNO_Keyboard_HID_version_03.html)
 * [Arduino-usbserial-uno.hex (Arduino Original firmware)](http://dl.dropbox.com/u/1816557/Arduino-usbserial-uno.hex)

##### Setting up guide :
* Boot to DFU Mode :  [Youtube Guide](https://www.youtube.com/watch?v=E8XyRwXQr8Q)
* Flash original Arduino UNO Firmware
```shell
sudo dfu-programmer atmega16u2 erase --force
sudo dfu-programmer atmega16u2 flash 'Arduino-usbserial-uno.hex'
sudo dfu-programmer atmega16u2 reset
```
* Upload <i>code.ino</i> to your arduino
* Flash Arduino Keyboard Firmwere
```shell
sudo dfu-programmer atmega16u2 erase --force
sudo dfu-programmer atmega16u2 flash 'Arduino-keyboard-0.3.hex.hex'
sudo dfu-programmer atmega16u2 reset
```
<hr />

### Code Guide
#### Press key
```Objective-C
keyPress(0, <Keycode>); 
```
##### Example
```Objective-C
keyPress(LEFT_GUI, 0x15); // Press R Key
```
#### Press Multiple key
```Objective-C
keyPress(<Modifier Key>, <KeyCode>);
```
##### Example
```Objective-C
keyPress(LEFT_GUI, 0x15); // Press Windows Key + R
```
#### Release Key
```Objective-C
keyRelease();
```
#### Write Text
```Objective-C
keyString(<Text>);
```
##### Example
```Objective-C
keyString("Hello World!"); // Write Hello World
```

