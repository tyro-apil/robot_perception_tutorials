.. dummy documentation master file, created by
   sphinx-quickstart on Mon Nov 25 08:09:32 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. toctree::
   :titlesonly:
   :maxdepth: 2
   :caption: Contents:
   :hidden:

   getting_started
   camera_calibration
   camera_interfacing

Introduction
===================

These tutorials will be focused on **Robot Perception** stack like Image Processing, Photogrammetry and Computer Vision being focused on applications in the field of robotics. 
A camera interfacing section would be included to deal with specific devices like Depth cameras, Pi-cameras, USB cameras.
Apart from that we will be focusing on problem specific algorithms and their implementations.

The idea of **Robot Perception** revolves around the question of **"What is Where?"**.  
For example: You want to pickup a blue ball. So, at first you need to perceive your surrounding i.e.
**"What does surrounding look like?"**" As per now, we can say surrouding consists of different colored balls.  
Then, we need to know the location of those balls in our real 3D world i.e. **"Where are the balls located?"**"  
The location is 3D coordinate with respect to a reference frame. Finally, we can complete our task to pickup a blue ball.

.. subfigure:: A|B
   :gap: 8px
   :subcaptions: below
   :name: robot_perception_introduction
   :class-grid: outline

   .. image:: _static/images/examples/obj_detection.jpg
      :alt: RGB image of surrounding

   .. image:: _static/images/examples/rviz_visualization.png
      :alt: Robot's understanding of its surrounding

   Robot Perception Introduction