Camera Model
=============

Pinhole Camera Model
--------------------

.. image:: /_static/images/camera_calib/pinhole_intuition.png

*Fig: Pinhole Camera Model Intuition* -- Source: `Wikipedia_Pinhole_Model`_

.. image:: /_static/images/camera_calib/pinhole_camera.png

*Fig: Pinhole Camera Model Intuition* -- Source: `Nvidia_Docs`_

Coordinate System
^^^^^^^^^^^^^^^^^

1. X\ :sub:`w`, Y\ :sub:`w`, Z\ :sub:`w` : World Coordinate Frame (Reference Frame)
2. X\ :sub:`c`, Y\ :sub:`c`, Z\ :sub:`c` : Camera Coordinate Frame
3. u, v : Pixel Coordinate Frame

World Frame (Convention)
""""""""""""""""""""""""
Generally, it would be a **robot’s base_link** or  a **map frame**

1. X\ :sub:`w`: Front
2. Y\ :sub:`w`: Left
3. Z\ :sub:`w`: Up

Camera Frame (Convention)
"""""""""""""""""""""""""
If camera lens is facing opposite to me, then:

1. Centre of lens: Origin
2. X\ :sub:`c`: Left -> Right
3. Y\ :sub:`c`: Top -> Bottom
4. Z\ :sub:`c`: Into the Plane

Pixel Frame (Convention)
"""""""""""""""""""""""""
If camera lens is facing opposite to me, then:

1. Top-left of the frame: Origin
2. u: Left -> Right
3. v: Top -> Bottom


Forward Projection
------------------

To **get the pixel coordinates** from the world coordinates

.. math::

   \mathbf{s} = \mathbf{K} \cdot [\mathbf{R} \mid \mathbf{t}] \cdot \mathbf{X}

where:

- :math:`\mathbf{s} = \lambda \begin{bmatrix} u \\ v \\ 1 \end{bmatrix}` (Homogeneous image coordinates)
- :math:`\mathbf{K} = \begin{bmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix}` (Intrinsic matrix: Camera -> Pixel Coordinates)
- :math:`[\mathbf{R} \mid \mathbf{t}] = \begin{bmatrix} r_{11} & r_{12} & r_{13} & t_1 \\ r_{21} & r_{22} & r_{23} & t_2 \\ r_{31} & r_{32} & r_{33} & t_3 \end{bmatrix}` (Extrinsic matrix: World -> Camera Coordinates)
- :math:`\mathbf{X} = \begin{bmatrix} X \\ Y \\ Z \\ 1 \end{bmatrix}` (Homogeneous world coordinates)


Role of each factor
^^^^^^^^^^^^^^^^^^^

Extrinsic Matrix -- :math:`[\mathbf{R}_{3x3} \mid \mathbf{t}_{3x1}]`
"""""""""""""""""""""""""""""""""""""""""""""""""""""

The three columns of rotation matrix :math:`\mathbf{R}`\ :sub:`3x3` represent the three basis vectors of camera frame with respect to world frame.
The translation vector :math:`\mathbf{t}`\ :sub:`3x1` represents the translation of camera frame with respect to world frame

Intrinsic Matrix -- :math:`\mathbf{K}_{3x3}`
"""""""""""""""""""""""""""""""""""
f\ :sub:`x` and f\ :sub:`y` are in diagonal position and convert units from **meters** to **pixels**.
During manufacturing, the sensor may not be square, so there's need of different values of f\ :sub:`x` and f\ :sub:`y`.

.. math::

   \mathbf{f_x} = \frac{\text{focal length in mm}}{\text{pixel size in mm per pixel (x axis)}}

c\ :sub:`x` and c\ :sub:`y` are the offsets in X & Y axis of the optical centre, where optical axis cuts the focal plane,
with respect to pixel coordinate frame. Ideally, the optical centre should be at the geometrical centre of the focal plane,
but due to errors in manufacturing, the axis may not pass exactly through centre in most cases but is quite near to the centre.


Backward Projection
-------------------

To get **world coordinates** from pixel coordinates. In most real world scenarios,
this is what we want to do instead of forward projection. During image formation, 
we project 3D scene to a 2D plane thus losing information of a dimension. So for backward projection
, we need to have information about the lost dimension i.e. **depth value of each image coordinate**
to get a unique solution (**single world coordinate**) using pixel coordinates.

For such use case, we use :ref:`depth cameras <depth_cameras>` that provides Z\ :sub:`c` i.e. z-coordinate
w.r.t. camera frame.

Distortion
----------
Due to spherical structure of lens, the image clicked from camera suffers from
unwanted distortions such that we donot obtain perfectly rectangular image as seen
by our eyes. Such distortion can be omitted by calibrating the camera.

.. image:: /_static/images/camera_calib/distortion_viz.png

*Fig: Common types of distortions in image* -- Source: `GFG_Distortion_Examples`_


.. _Wikipedia_Pinhole_Model: https://en.wikipedia.org/wiki/Pinhole_camera_model#/media/File:Pinhole-camera.svg
.. _Nvidia_Docs: https://docs.nvidia.com/vpi/appendix_pinhole_camera.html
.. _GFG_Distortion_Examples: https://media.geeksforgeeks.org/wp-content/uploads/20230428155936/Distortion.webp