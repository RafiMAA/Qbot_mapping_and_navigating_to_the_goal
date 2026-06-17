Terminal 1: Launch the Hardware Stack
This will connect to the Kobuki base, spin up the LD19 LiDAR, start the SLAM mapping, and launch your A* Navigation Server.


cd ~/Desktop/ROS2_Final_Project/kobuki_ws
source /opt/ros/jazzy/setup.bash
source install/setup.bash
ros2 launch qbot_nav qbot_hardware.launch.py


Terminal 2: Start the WebSocket Bridge
This opens the radio channel so the React UI can talk to ROS 2.


cd ~/Desktop/ROS2_Final_Project/kobuki_ws
source /opt/ros/jazzy/setup.bash
source install/setup.bash
ros2 run rosbridge_server rosbridge_websocket --ros-args -p port:=9090


Terminal 3: Serve the React UI
This hosts your compiled React app on a lightweight, lightning-fast Python web server.


cd ~/Desktop/ROS2_Final_Project/build
python3 -m http.server 8000
