# Magicbot-Z1 Description (URDF & MJCF)

## Overview

This package includes a universal humanoid robot description (URDF & MJCF) for the [Magicbot-Z1](https://www.magiclab.top/z1), developed by Magiclab Robotics.

<table>
  <tr>
    <td><img src="doc/rviz.png" width="400"/></td>
    <td><img src="doc/mujoco.png" width="400"/></td>
  </tr>
</table>

Magicbot-Z1 Humanoid has 23 actuated joints (plus a floating base):

```text
root [⚓] => /pelvis/  (floating_base)
    left_hip_pitch_joint [⚙+Y] => /left_hip_pitch_link/
        left_hip_roll_joint [⚙+X] => /left_hip_roll_link/
            left_hip_yaw_joint [⚙+Z] => /left_hip_yaw_link/
                left_knee_joint [⚙+Y] => /left_knee_link/
                    left_ankle_pitch_joint [⚙+Y] => /left_ankle_pitch_link/
                        left_ankle_roll_joint [⚙+X] => /left_ankle_roll_link/
    right_hip_pitch_joint [⚙+Y] => /right_hip_pitch_link/
        right_hip_roll_joint [⚙+X] => /right_hip_roll_link/
            right_hip_yaw_joint [⚙+Z] => /right_hip_yaw_link/
                right_knee_joint [⚙+Y] => /right_knee_link/
                    right_ankle_pitch_joint [⚙+Y] => /right_ankle_pitch_link/
                        right_ankle_roll_joint [⚙+X] => /right_ankle_roll_link/
    waist_yaw_joint [⚙+Z] => /torso_link/
        left_shoulder_pitch_joint [⚙+Y] => /left_shoulder_pitch_link/
            left_shoulder_roll_joint [⚙+X] => /left_shoulder_roll_link/
                left_shoulder_yaw_joint [⚙+Z] => /left_shoulder_yaw_link/
                    left_elbow_joint [⚙+Y] => /left_elbow_link/
                        left_wrist_roll_joint [⚙+X] => /left_wrist_roll_link/
                            left_hand_palm_link (fixed)
        right_shoulder_pitch_joint [⚙+Y] => /right_shoulder_pitch_link/
            right_shoulder_roll_joint [⚙+X] => /right_shoulder_roll_link/
                right_shoulder_yaw_joint [⚙+Z] => /right_shoulder_yaw_link/
                    right_elbow_joint [⚙+Y] => /right_elbow_link/
                        right_wrist_roll_joint [⚙+X] => /right_wrist_roll_link/
                            right_hand_palm_link (fixed)
        head_joint [⚙+Z] => /head_link/
```

## Files

| Type | Path | Description |
| --- | --- | --- |
| URDF | [`urdf/MagicBotZ1.urdf`](urdf/MagicBotZ1.urdf) | Robot description for ROS 2 / RViz, meshes referenced via `package://magicbot-z1_description/meshes/` |
| MJCF | [`mjcf/MAGICBOTZ1.xml`](mjcf/MAGICBOTZ1.xml) | MuJoCo model, meshes referenced via `meshdir="../meshes"` |
| Meshes | [`meshes/`](meshes) | STL meshes shared by URDF and MJCF |
| Launch | [`launch/view.launch.py`](launch/view.launch.py) | RViz viewer launch file |
| RViz | [`rviz/view.rviz`](rviz/view.rviz) | RViz preset configuration |

## Usages

### RViz
```bash
sudo apt install ros-humble-joint-state-publisher-gui
cd magicbot-z1_description
colcon build --packages-select magicbot-z1_description
source install/setup.bash
ros2 launch magicbot-z1_description view.launch.py
```

### MuJoCo
```bash
pip install mujoco
cd magicbot-z1_description
python3 -m mujoco.viewer --mjcf=mjcf/MAGICBOTZ1.xml
```

Or with the MuJoCo `simulate` binary:
```bash
./simulate mjcf/MAGICBOTZ1.xml
```
