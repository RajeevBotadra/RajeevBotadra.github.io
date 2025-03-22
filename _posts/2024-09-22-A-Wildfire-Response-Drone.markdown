---
#layout: single
title: "Wildfire Response Drone"
date: 2024-09-22
categories: projects
excerpt: "Developing a UAV for wildfire surveillance."
---
<style>
  body {
    font-family: "Calibri", sans-serif;
    font-size: 20px;
  }
</style>

![Wildfire in Maderna County, CA](/assets/images/posts/wildfire-response-drone/ECE414_Report_WILDFIRE.PNG)

### Abstract
Wildfires have become a growing risk over recent years, endangering vast regions of wildlife and the health of
nearby communities. Traditional fire suppression methods are expensive and often fail to contain large-scale
fires, resulting in the release of massive amounts of pollutants and the destruction of land. We address this
threat by creating an Unmanned Aerial Vehicle (UAV) system equipped with Computer Vision technology
for the early detection and assisted suppression of wildfires. In designing the UAV, we outline three key
objectives: (1) Autonomous patrols of regions of interest (ROI) to monitor and detect wildfire threats to a
base station, (2) Real-time assistance in active firefighting efforts by relaying a birds-eye-view to the on-site
personnel, (3) Coordinate estimation of heat spots during ongoing fires for Very-Large-Airtankers (VLATs)
drops.

![MaskRCNN Two-Shot Semantic Segmentation](/assets/images/posts/wildfire-response-drone/ECE417_MaskRCNN_A.PNG)

The drone consists of a Pixhawk computer for flight control, an Nvidia Jetson Nano companion computer for real-time object detection, a Full-HD camera, telemetry sensors, a Lithium battery, a radio transmitter-receiver, and a propulsion system (including propellers, electronic speed circuits, motors). The Nano uses a fine-tuned
Mask R-CNN model for real-time object detection and semantic segmentation from the camera feed. The
model was tuned on manually annotated video data from drone flyovers of wildfires and detects smoke and
fires (classifying them and creating bounding boxes around the region). The model achieves 95% accuracy in classifying fire and smoke and 87% accuracy in producing appropriate bounding boxes around the regions of interest (fire, smoke). The drone has been tested working in manual flight mode (with a remote-control) and pre-planned mode (follow pre-planned trajectories) with ongoing testing in autonomous mode (flight controlled by Jetson Nano according to camera, GPS, and accelerometer data).

