# AI-Virtual-Keyboard
This is the project made by Vinit Mehra, Linu Shibu, and Siddharth Sawhney for the Artificial Intelligence Course.
In this project, we have tried to reduce the gap between the real world and the augmented environment to produce a mixed-reality system. 
For that purpose, we created a virtually controllable keyboard system which is created and implemented using OpenCV libraries and Python. 
To provide an easy immersive augmented experience that is also gesture-enabled, we employ a web camera that is integrated with OpenCV libraries through a compiler. 
Using our system, users can control a virtual keyboard using their finger movements and fingertips.

This project describes the way of implementing a virtual keyboard without any additional hardware but by using the webcam available in the system. The webcam simply captures the consecutive frames and compares them to recognize it as a click if there is a difference in the contour

## Issue in existing system

One of the rising problems with VR industry is there aren't many devices which are being utilized for helping disabled or especially abled people. Recent years have marked a sharp increase in the number of ways in which people interact with computers. Where the keyboard and mouse were once the primary interfaces for controlling a computer, users now utilize touch screens, infrared cameras, and accelerometers (for example, within the iPhone) to interact with their technology.

## Problem statement
In light of these changes and the proliferation of small cameras in many phones and tablets, human-computer interface researchers have investigated the possibility of implementing a keyboard style interface using a camera as a substitute for actual keyboard hardware.

The camera may observe the hands from above the surface, or at an angle. The virtual keyboard’s software analyses those images in real-time to determine the sequence of keystrokes chosen by the user.

## Objective
+ To make a virtual keyboard which can type letters from detecting our hands.
+ With the help of opencv, mediapipe and cvzone make functions such that they can recognize hand position and gesture of when it is clicked.
+ With the help of pynput, print the selected letters to the selected cursor point.
+ Moving away from primitive methods of physical input technologies like mechanical keyboards.

## Proposed Methodology
### Keyboard Layout Model
First of all, we make an array of the keyboard layout we want to display, i.e. , the QWERTY layout. To display that, we use the cv2.rectangle function to create a semi-transparent virtual layout of the whole keyboard and superimpose it on the video feed.
### Palm Detection Model
Before using a hand detection model, we use a palm detection model by MediaPipe, since estimating bounding boxes of rigid objects like palms and fists is significantly simpler than detecting hands with articulated fingers. In addition, as palms are smaller objects, the non-maximum suppression algorithm works well even for two-hand self-occlusion cases, like handshakes. Moreover, palms can be modelled using square bounding boxes (anchors in ML terminology) ignoring other aspect ratios, and therefore reducing the number of anchors by a factor of 3-5.
### Hand Detection Model
After the palm detection over the whole image the subsequent hand landmark model (Again, done using MediaPipe in Python) performs precise keypoint localization of 21 3D hand-knuckle coordinates inside the detected hand regions via regression, i.e,  direct coordinate prediction. The model learns a consistent internal hand pose representation and is robust even to partially visible hands and self-occlusions.

![image](https://github.com/vinit714/AI-Virtual-Keyboard/assets/52816788/6a0fa029-c01d-4c9b-ae73-d4a63a1ea809)

### Click Detection
Using the landmarks given in the hand detection model, we use a distance measuring function called detector.findDistance between the landmark points 8 and 12 to detect a click. When the distance between the point 8 (index finger) and 12 (middle finger) is less than 30 pixels, the function registers it as a click and records it position. The position recorded is then used in analogous with the keyboard layout model to determine the key pressed, which in-turn is added to the final textbox.


## Screenshot of demo
![image](https://github.com/vinit714/AI-Virtual-Keyboard/assets/52816788/f90b74b9-a1c3-4fbc-b9cf-b693512c1daf)





