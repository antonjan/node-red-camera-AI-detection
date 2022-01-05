# node-red-camera-AI-detection
This projetc will have the code to monitor SSTV cameras and then detects a person and send alert to Telegram and to Google home.
# Dependincy
Install the following

     node red contributed tfjs coc ssd (tf coco ssd)
     I use mqtt to send message to a flow witch then send the message to telegram (seperate telegram flow)
     node red contributed cast (crome cast to google home)
     
## Screenshot of working flow
![Exsample flow](Camera_Person_detection.png?raw=true "Camera AI flow")<br>

Import the flow into your Node red <a href="flows(5).json">flows(5).json</a><br>

How to find you camera string using the windows app anycam.io (enable onvif scanning as well)
Add camera and enter its ip address it will then find the streaming string EG. rtsp://username:password@192.168.0.2:554/onvif1
![EAnycam](anycam-io.2.jpeg?raw=true "Anycam")<br>
You will the have to add the username and password of your camera as in exsample above and add the string to the exec node
    rtsp://username:password@192.168.0.2:554/onvif1
    
Edit the exec node and add the following "ffmpeg  -y -i "rtsp://username:password@192.168.0.2:554/onvif1" -vframes 1  /home/pi/2.jpg"<br>
In front

      ffmpeg  -y -i 
      
At the end 

      -vframes 1  /home/pi/2.jpg
      
then save

This will go and get an image from the camera and save it to a file home/pi/2.jpg<br>
Make sure that the file in node has the same path to the file <br>
The file in node will send the image to the AI (tf coco SSD)<br>
The rest of the nodes is strate forword.<br>
## Some settings you can play with
You need to play around with the <b>sThreshold > 0.6</b> setting in the function node if you get false readings (depends on your camera conditions)<br>
System takes images every 8s due to the GPU constrans in Rapberry pi you can play around with the timer in the inject node or you can make it loop when it is finshed

## Exsample of telegram message
![Telegram message](ai_person_detect.png?raw=true "Telegram message")<br>
