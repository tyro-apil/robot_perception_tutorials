Getting Started
================

.. contents:: Contents
  :local:
  :depth: 2

We now begin with introducing with the cameras, programming languages and libraries that we will be using throughout this tutorial series.

Cameras
------------

In Robotics Club Pulchowk, we have used `OAK-D Pro W`_ Camera as a vision sensor for Automatic Robot of ABU Robocon 2024.
We also used `Pi Camera Module 3 Wide`_ interfaced with Raspberry Pi 4B with Raspian OS (through CSI Camera Port). Moreover,
similar applications are possible with USB cameras like `Logitech C270`_.

Depth Cameras
^^^^^^^^^^^^^
.. _depth_cameras:

.. image:: _static/images/cameras/oakd_pro_w.webp

*Fig: OAK-D Pro W Camera*

Monocular RGB Cameras
^^^^^^^^^^^^^^^^^^^^^

.. image:: _static/images/cameras/pi_cam_v3_wide.jpg

*Fig: Raspberry Pi Camera v3 Wide*

.. image:: _static/images/cameras/logitech.webp

*Fig: Logitech C270 HD Webcam*


Software Stack
---------------

We will be using Python and MATLAB/Octave languages extensively. 
And, OpenCV, Numpy and Scipy libraries will be used in Python.
For MATLAB, Computer Vision toolbox is used.

.. list-table::
   :align: center
   :class: image-grid

   * - .. figure:: /_static/images/logos/python_logo.png
          :width: 150
          :alt: Python

          **Python**

     - .. figure:: /_static/images/logos/matlab_logo.png
          :width: 150
          :alt: Matlab

          **Matlab**

     - .. figure:: /_static/images/logos/octave_logo.jpeg
          :width: 150
          :alt: Octave

          **Octave**
          
.. toctree::
  :maxdepth: 2
  :caption: Chapters

  getting_started/setup
  getting_started/mathematics_refresher




.. _OAK-D PRO W: https://docs.luxonis.com/hardware/products/OAK-D%20Pro%20W
.. _Pi Camera Module 3 Wide: https://www.raspberrypi.com/products/camera-module-3/?variant=camera-module-3-wide
.. _Logitech C270: https://www.logitech.com/en-us/shop/p/c270-hd-webcam
