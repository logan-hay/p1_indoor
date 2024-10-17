### TO INSTALL PACKAGE FOR ASSIGNMENT 

1. Set up environment variables for ROS. Make sure to replace '/home/rpi/shared' with your own shared folder location
<pre>
source /opt/ros/humble/setup.bash
</pre>
Also do any Windows or Mac specific setup

For example in Mac...
<pre>
export WEBOTS_HOME=/Applications/Webots.app
python3 local_simulation_server.py
</pre>

For example in windows...
<pre>
export WEBOTS_HOME=/mnt/c/Program\ Files/Webots
</pre>

2. Fork your own repository of this project (using web interface)

3. Clone your fork
<pre>
git clone <your github url for this repository>
</pre>

4. Make the package (for python, it really just installs the files)
<pre>
cd p1_indoor
colcon build
</pre>

5. Set up variables to use the package you just created
<pre>
source install/setup.bash
</pre>

6. Start webots simulation with connect back to ROS in the virtual machine
<pre>
ros2 launch indoor_simulation indoor_simulation_launch.py
</pre>

### Recomendations
Due to the complexity of the simulation, I recommend openning Webots prior to trying to run the simulation and changing the following settings

1. Start up project in a paused state
<pre>
Tools > Preferences > General > Startup Mode: Pause, Rendering: Off
</pre>

2. Start up project in a paused state
<pre>
Tools > Preferences > OpenGL > Texture Quality: Low
</pre>

3. Line 20 in "RidgecrestWest.wbt" sets the basicTimeStep to 32. Increasing this value will reduce the strain but update the simmulation at a slower rate. It may be preferable to decrease this value for a worse performance but a more accurate result.
<pre>
WorldInfo {
  basicTimeStep 32
}
</pre>