# estherag_intro_cognitive_archs_pixi

## Status

It builds.

And Mirte moves in Gazebo.

## Building

Note: the Pixi environment and Colcon workspace will require approximately 13 GB of free disk space.

### Linux

- install Pixi ([docs](https://pixi.prefix.dev/latest/installation/))
- clone [gavanderhoorn/estherag_intro_cognitive_archs_pixi](https://github.com/gavanderhoorn/estherag_intro_cognitive_archs_pixi) *somewhere* (on a disk with sufficient free space)

Then:

```bash
cd /path/to/estherag_intro_cognitive_archs_pixi
pixi install
pixi run fetch
touch src/deps/mirte-ros-packages/mirte_telemetrix_cpp/COLCON_IGNORE
pixi shell
colcon build
source install/setup.bash
```

At this point all packages in the Colcon workspace should be available.

Running `ros2 launch cognitive_nav mirte_house.launch.py` should start Gazebo and show Mirte in the living room.


## Known issues

### missing `libgazebo_grasp_fix.so`

```
[gazebo-1] [Err] [SystemLoader.cc:92] Failed to load system plugin [libgazebo_grasp_fix.so] : Could not find shared library.
```

It's unclear where this package should be sourced from -- or whether it's even still used.

### TypeError: only 0-dimensional arrays can be converted to Python scalars

This could be an incompatibility between Python 3.12 (as installed by Pixi) and the `tracking_node` script in `yolo_ros`.
