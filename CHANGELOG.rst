^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package openni2_camera
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.3.1 (2019-10-01)
------------------
* Fix deprecated pluginlib call
* Contributors: Victor Lopez

0.3.0 (2018-05-22)
------------------
* Merge pull request `#11 <https://github.com/pal-robotics-forks/openni2_camera/issues/11>`_ from uts-magic-lab/improve_tf_skeletons
  Improve the TF of the skeletons
* Merge pull request `#10 <https://github.com/pal-robotics-forks/openni2_camera/issues/10>`_ from pal-robotics-forks/create-user-tracker-only-when-no-failing
  Create user tracker only when no failing
* Improve the TF of the skeletons
  Now publishing the TF is optional (dynamic reconfigure), as it may get expensive in CPU & network traffic.
  Also all the transforms are published in one single publication call from the same transform broadcaster. This lowers the publication from 500hz to 50Hz... and that's with one skeleton, there can be up to 4 I think.
  Also now the tf frames have a number appended to them to keep track of which is which (otherwise two users would have the same frames and they would jump like crazy).
* check if getUserTracker is OK
* getUserTracker no longer throws and returns bool
* add std::cout verbose messages for errors
* print firmware version when initializing
* Merge pull request `#9 <https://github.com/pal-robotics-forks/openni2_camera/issues/9>`_ from pal-robotics-forks/disable-completely-rgb-processing-when-needed
  Disable completely rgb processing when requested
* diable RGB processing when desired
* Merge pull request `#8 <https://github.com/pal-robotics-forks/openni2_camera/issues/8>`_ from v-lopez/fix-skeleton-tracker-frame
  Skeleton tracker's tf will use depth frame instead of hard coded one
* Skeleton tracker will use depth frame instead of hard coded one
* Merge pull request `#7 <https://github.com/pal-robotics-forks/openni2_camera/issues/7>`_ from pal-robotics-forks/rm-pal-vision-msgs
  stop using pal vision msgs and use pal_detection_msgs
* use pal_detection_msgs rather than pal_vision_msgs
* lower some ROS_INFO to ROS_debug
* Merge pull request `#5 <https://github.com/pal-robotics-forks/openni2_camera/issues/5>`_ from v-lopez/indigo-devel
  Indigo devel
* Fix mirroring of depth image
* Merge branch 'hydro-devel' into indigo-devel
  Conflicts:
  CHANGELOG.rst
  CMakeLists.txt
  include/openni2_camera/openni2_driver.h
  package.xml
  src/openni2_device.cpp
  src/openni2_driver.cpp
* Merge pull request `#4 <https://github.com/pal-robotics-forks/openni2_camera/issues/4>`_ from v-lopez/hydro-devel
  Add missing link dependency
* Merge commit 'ffaa5d1' into hydro-devel
* Add commands to build debians
* Don't use libraries embedded in the package. Use system ones.
* Merge pull request `#46 <https://github.com/pal-robotics-forks/openni2_camera/issues/46>`_ from taketwo/add-exposure-control
  Add exposure time control
* Merge pull request `#47 <https://github.com/pal-robotics-forks/openni2_camera/issues/47>`_ from mintar/fix_resolve_device_uri
  Fix resolveDeviceURI: <bus>@<devicenr> format, don't connect if invalid
* Add missing link dependency
* Make <bus>@<devicenr> device_id format work
  Without this patch, things like `device_id = '2@0'` worked (meaning
  any device on bus 2), but `device_id = '2@8'` (meaning device number 8
  on bus 2) didn't.
* Don't connect to any device if URI cannot be resolved
  Fixes `#35 <https://github.com/pal-robotics-forks/openni2_camera/issues/35>`_.
* Merge pull request `#3 <https://github.com/pal-robotics-forks/openni2_camera/issues/3>`_ from v-lopez/add-user-tracking
  Add fixes and publication of user tracker transforms
* Add exposure time control
  This commit adds getter/setter methods for exposure time and a dynamic
  reconfigure option to manipulate this setting.
* Don't use libraries embedded in the package. Use system ones.
* Publish user tracker transforms
* Always connect to user tracker, only publish if there are subscribers
* Add NiTE ini required to use NiTE tracking
* add alternative way to compute world points
* publish camera rgb pose wrt /base_link
  This data is included in person_detection_msgs::PersonDetections::camera_pose
  A tf::TransformListener has been added in order to get this transformation
* set user Id to face.name of PersonDetection.msg
* Merge pull request `#2 <https://github.com/pal-robotics-forks/openni2_camera/issues/2>`_ from jordi-pages/patch-1
  Fix link to user_map image example
* Fix link to user_map image example
* Merge pull request `#1 <https://github.com/pal-robotics-forks/openni2_camera/issues/1>`_ from pal-robotics/add_user_tracker
  Add user tracker
* Document /camera/users topic
* publish persons position wrt RGB-D camera
* Merge branch 'add_user_tracker' of https://github.com/pal-robotics/openni2_camera into add_user_tracker
* draw skeletons in user map
* Update README.md
  center user map example image
* Merge branch 'add_user_tracker' of https://github.com/pal-robotics/openni2_camera into add_user_tracker
* add example image of user map
* Update README.md
  add instructions to visualize the user map
* added modified files
* add nite::UserTracker successfully
  two topic added:
  /camera/num_users: number of users being tracked
  /camera/user_map: image showing segmented users each one painted in a different color
* cppcheck exception
* add missing installation rules
  add installation rules for lib/libOpenNI2.so, lib/libNiTE2.so lib/OpenNI2
  add print warning about NiTE2 initialisation
* Add missing instruction to visualize depth image
* Merge branch 'hydro-devel' of github.com:jordi-pages/openni2_camera into hydro-devel
* fix HandTracker::readFrame crash
  The HandTracker::readFrame works well during the lifetime of the first subscriber to /camera/gestures. Nevertheless, when this subscriber shutsdown and a new subscriber connects the first call to HandTracker::readFrame crashes.
  It seems that it is not possible to robustly stop and re-start the HandTracker. Work-around implemented trying to minimise the CPU consumption when there are no subscribers
* Complete documentation
* Improve formatting
* Integrate NiTE2 for gesture recognition
  Integrate NiTE2 to add a hand tracker to perform gesture recognition (waving and clicking)
  Add headers and binaries of OpenNI 2.2.0.33 and NiTE 2.2.0.10
  Add ~<camera>/gestures topic where pal_vision_msgs/Gesture is published everytime a hand-based gesture is recognized
  Fix few cppcheck errors
* Contributors: Adria Roig, Daniel Pinyol, Jordi Pages, Martin Guenther, Michael Ferguson, Sammy Pfeiffer, Sergey Alexandrov, Victor Lopez

0.2.7 (2016-06-07)
------------------
* Merge pull request `#44 <https://github.com/ros-drivers/openni2_camera/issues/44>`_ from jacquelinekay/fix_kinetic_build
  fix compile on kinetic
* Contributors: Jackie Kay, Michael Ferguson

0.2.6 (2016-05-05)
------------------
* [fix] Compile for OSX `#30 <https://github.com/ros-drivers/openni2_camera/issues/30>`_
* [fix] Crash on OSX and warning fixes.
* Contributors: Hans Gaiser, Isaac I.Y. Saito, Michael Ferguson

0.2.5 (2015-10-15)
------------------
* Merge pull request `#34 <https://github.com/ros-drivers/openni2_camera/issues/34>`_ from Intermodalics/feature/get_serial_service
  added get_serial service
* Contributors: Michael Ferguson, Ruben Smits

0.2.4 (2015-04-06)
------------------
* proper usage of device_id parameter in resolveDeviceURI, resolve unique parts of device URIs, too
* print vendor id and product id as hex value (like in lsusb)
* Contributors: Michael Ferguson, Stephan Wirth

0.2.3 (2015-01-16)
------------------
* Explicitly ask for serial number when trying to resolve device URI instead of doing it once on device connected, fixes `#24 <https://github.com/ros-drivers/openni2_camera/issues/24>`_
* Contributors: Michael Ferguson, Stephan Wirth

0.2.2 (2014-10-06)
------------------
* Add usb_reset
* Contributors: Kei Okada, Michael Ferguson

0.2.1 (2014-08-22)
------------------
* Fixed a bug that prevents depth only sensors from properly calculating the point cloud due to incorrect focal length
* Updated cmakelists for OSX
* Contributors: Colin Lea, Michael Ferguson, Tarek Taha

0.2.0 (2014-05-22)
------------------
* device_id: find camera by serial number
* Make freenect_stack link a real link for wiki.
* Contributors: Dariush Forouher, Michael Ferguson

0.1.2 (2014-02-03)
------------------
* Fix CMake error.
* Contributors: Benjamin Chretien, Michael Ferguson

0.1.1 (2013-11-13)
------------------
* Fixed default value of ir_mode. Thanks @nxdefiant
  https://github.com/ros-drivers/openni2_camera/issues/16

0.1.0 (2013-08-28)
------------------
* initial release
