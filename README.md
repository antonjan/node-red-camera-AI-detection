# node-red-camera-AI-detection
This projetc will have the code to monitor SSTV cameras and then detects a person and send alert to Telegram and to Google home.
![Exsample flow](Camera_Person_detection.png?raw=true "Camera AI flow")<br>

How to find you camera string using the windows app anycam.io (enable onvif scanning as well)
Add camera and enter its ip address it will then find the streaming string EG. rtsp://username:password@192.168.0.2:554/onvif1

You will the have to add the username and password of your camera as in exsample above and add the string to the exec node

