# Smart Device for Visually Impaired Individuals

## What is this?

Our device is designed to assist individuals with visual impairments, including those who are blind or legally blind, by providing real-time object detection and distance estimation. For a more detailed overview, please look at the research poster located in the **docs/** folder. Click the image below to see a video demo!

[![Watch the video](https://img.youtube.com/vi/zgXAb3tXPgo/hqdefault.jpg)](https://www.youtube.com/shorts/zgXAb3tXPgo)

## Device Configuration

For the creation of this device, we combined the following objects onto a helmet:
* Raspberry Pi
* STM32
* Arducam ToF Camera
* USB Wide Angle Camera
* Button
* Earbuds
* Battery pack

## Navigation

For the navigation side of our project, we wanted it to be able to run on our wearable, while also not allocating too many resources. Additionally, we wanted it to run locally so that the user would not have to worry about connectivity issues. For these reasons we implemented OSMnx for our path planning algorithm. This allows us to:
* Have a offline path planning algorithm that can run on the Raspberry Pi from anywhere
* Lightweight, allowing for it to run simultaneously with other scripts on the Raspberry Pi while also not stunting their performance.
* Also allows for full customization of the program so that we could add things like realtime GPS location and walking velocity if we wanted too.

## Object Avoidance

For our Object Avoidance, we decided to use an Arducam ToF camera. This type of camera allows us to determine object distances at a pixel level. How it works is by measuring the time it takes for a light signal to travel from the camera to an object and back. This method allows us to:
* Detect different objects at different levels. Useful for cases in which a very thin, low, or high object approaches the wearer.
* Cheaper than a  lidar sensor while being more accurate, considering we only care about what is in front of the wearer.
* Easier to mount, we can utilize it’s camera shape to mount next to the wide angle camera, allowing us to save room on the helmet for the Raspberry Pi and the STM32.

## Object Detection

For Object Detection, we chose to use the YOLO (You Only Look Once) model. This deep learning based object detection framework allows us to identify and classify objects in real time. This method allows us to:
* Detect multiple objects simultaneously, ensuring objects such as traffic signs, stop signs, and other street cues are recognized.
* Operate efficiently on embedded hardware, as YOLO’s optimized architecture ensures low-latency inference, making it possible to run on a system powered by a Raspberry Pi.