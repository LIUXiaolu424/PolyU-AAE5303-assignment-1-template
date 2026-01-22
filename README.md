# AAE5303 Environment Setup Report

> **Important:** Follow this structure exactly in your submission README.  
> Your goal is to demonstrate **evidence, process, problem-solving, and reflection** — not only screenshots.

---

## 1. System Information

**Laptop model:**  
_[LENOVO ThinkPad T14p Gen 2]_

**CPU / RAM:**  
_[Intel(R) Core(TM) Ultra 9 185H]_

**Host OS:**  
_[Windows 11]_

**Linux/ROS environment type:**  
_[Choose one:]_
- [ ] Dual-boot Ubuntu
- [√] WSL2 Ubuntu
- [ ] Ubuntu in VM (UTM/VirtualBox/VMware/Parallels)
- [ ] Docker container
- [ ] Lab PC
- [ ] Remote Linux server

---

## 2. Python Environment Check

### 2.1 Steps Taken

Describe briefly how you created/activated your Python environment:

**Tool used:**  
_[venv]_

**Key commands you ran:**
```bash
source /opt/ros/foxy/setup.bash
source /root/PolyU-AAE5303-env-smork-test/ros2_ws/install/setup.bash
source /root/PolyU-AAE5303-env-smork-test/.venv/bin/activate    
```

**Any deviations from the default instructions:**  
_[None, perfect instructions and template]_

### 2.2 Test Results

Run these commands and paste the actual terminal output (not just screenshots):

```bash
python scripts/run_test_python_env.py
```

**Output:**
```
=== Summary ===
✅ Environment: {
  "platform": "Linux-6.6.87.2-microsoft-standard-WSL2-x86_64-with-glibc2.31",
  "python": "3.10.13",
  "executable": "/root/PolyU-AAE5303-env-smork-test/.venv/bin/python",
  "cwd": "/root/PolyU-AAE5303-env-smork-test",
  "ros": {
    "ROS_VERSION": "2",
    "ROS_DISTRO": "foxy",
    "ROS_ROOT": null,
    "ROS_PACKAGE_PATH": null,
    "AMENT_PREFIX_PATH": "/root/PolyU-AAE5303-env-smork-test/ros2_ws/install/env_check_pkg:/opt/ros/foxy",
    "CMAKE_PREFIX_PATH": "/root/PolyU-AAE5303-env-smork-test/ros2_ws/install/env_check_pkg"
  }
}
✅ Python version OK: 3.10.13
✅ Module 'numpy' found (v2.2.6).
✅ Module 'scipy' found (v1.15.3).
✅ Module 'matplotlib' found (v3.10.8).
✅ Module 'cv2' found (v4.12.0).
✅ Module 'rclpy' found (vunknown).
✅ numpy matrix multiply OK.
✅ numpy version 2.2.6 detected.
✅ scipy FFT OK.
✅ scipy version 1.15.3 detected.
✅ matplotlib backend OK (Agg), version 3.10.8.
✅ OpenCV OK (v4.12.0), decoded sample image 128x128.
✅ Open3D OK (v0.19.0), NumPy 2.2.6.
✅ Open3D loaded sample PCD with 8 pts and completed round-trip I/O.
✅ ROS 2 CLI OK: /opt/ros/foxy/bin/ros2
✅ ROS 1 tools not found (acceptable if ROS 2 is installed).
✅ colcon found: /usr/bin/colcon
✅ ROS 2 workspace build OK (env_check_pkg).
✅ ROS 2 runtime OK: talker and listener exchanged messages.
✅ Binary 'python3' found at /root/PolyU-AAE5303-env-smork-test/.venv/bin/python3

All checks passed. You are ready for AAE5303 🚀
✅ Python + ROS environment checks: PASS (19.4s)

========== Step 2: Open3D point cloud pipeline ==========
Running: /root/PolyU-AAE5303-env-smork-test/.venv/bin/python -u /root/PolyU-AAE5303-env-smork-test/scripts/test_open3d_pointcloud.py
ℹ️ Loading /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.
✅ Open3D point cloud pipeline: PASS (3.8s)

ℹ️ Cleaned up 1 generated file(s) in data/.

========================================
OVERALL RESULT: PASS
========================================
```

```bash
python scripts/test_open3d_pointcloud.py
```

**Output:**
```
 Loading /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /root/PolyU-AAE5303-env-smork-test/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.
```

**Screenshot:**  

<img width="1614" height="616" alt="image" src="https://github.com/user-attachments/assets/19b2fae9-94d4-4805-8926-cee085bddd80" />

---

## 3. ROS 2 Workspace Check

### 3.1 Build the workspace

Paste the build output summary (final lines only):

```bash
source /opt/ros/foxy/setup.bash
colcon build
```

**Expected output:**
```
Summary: 1 package finished [x.xx s]
```

**Your actual output:**
```
Starting >>> env_check_pkg
Finished <<< env_check_pkg [0.26s]                     

Summary: 1 package finished [0.66s]
```

### 3.2 Run talker and listener

Show both source commands:

```bash
source /opt/ros/humble/setup.bash
source install/setup.bash
```

**Then run talker:**
```bash
ros2 run env_check_pkg talker
```

**Output (3–4 lines):**
```
[INFO] [1769088809.696809200] [env_check_pkg_talker]: AAE5303 talker ready (publishing at 2 Hz).
[INFO] [1769088810.199903750] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #0'
[INFO] [1769088810.697056026] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #1'
[INFO] [1769088811.197172880] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #2'
[INFO] [1769088811.697210020] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #3'
```

**Run listener:**
```bash
ros2 run env_check_pkg listener
```

**Output (3–4 lines):**
```
root@d39598807ee7:~/PolyU-AAE5303-env-smork-test# ros2 run env_check_pkg listener
[INFO] [1769089227.029445074] [env_check_pkg_listener]: AAE5303 listener awaiting messages.
[INFO] [1769089317.697946695] [env_check_pkg_listener]: I heard: 'AAE5303 hello #0'
[INFO] [1769089318.197753845] [env_check_pkg_listener]: I heard: 'AAE5303 hello #1'
[INFO] [1769089318.742744666] [env_check_pkg_listener]: I heard: 'AAE5303 hello #2'
[INFO] [1769089319.197908409] [env_check_pkg_listener]: I heard: 'AAE5303 hello #3'
```

**Alternative (using launch file):**
```bash
ros2 launch env_check_pkg env_check.launch.py
```

**Screenshot:**  

<img width="1678" height="646" alt="Talker and Listner Running" src="https://github.com/user-attachments/assets/fd1e9ea5-d937-48a8-a2ed-54d81e67e7d9" />

---

## 4. Problems Encountered and How I Solved Them

> **Note:** Write 2–3 issues, even if small. This section is crucial — it demonstrates understanding and problem-solving.

### Issue 1: [Write the exact error message or problem]

**Cause / diagnosis:**  
_[Explain what you think caused it]_

**Fix:**  
_[The exact command/config change you used to solve it]_

```bash
[Your fix command/code here]
```

**Reference:**  
_[Official ROS docs? StackOverflow? AI assistant? Something else?]_

---

### Issue 2: [Another real error or roadblock]

**Cause / diagnosis:**  
_[Explain what you think caused it]_

**Fix:**  
_[The exact command/config change you used to solve it]_

```bash
[Your fix command/code here]
```

**Reference:**  
_[Official ROS docs? StackOverflow? AI assistant? Something else?]_

---

### Issue 3 (Optional): [Title]

**Cause / diagnosis:**  
_[Explain what you think caused it]_

**Fix:**  
_[The exact command/config change you used to solve it]_

```bash
[Your fix command/code here]
```

**Reference:**  
_[Official ROS docs? StackOverflow? AI assistant? Something else?]_

---

## 5. Use of Generative AI (Required)

Choose one of the issues above and document how you used AI to solve it.

> **Goal:** Show critical use of AI, not blind copying.

### 5.1 Exact prompt you asked

**Your prompt:**
```
解释一下这两句的作用(source /opt/ros/foxy/setup.bash, source /root/PolyU-AAE5303-env-smork-test/ros2_ws/install/setup.bash)
```

### 5.2 Key helpful part of the AI's answer

**AI's response (relevant part only):**
```
| 场景                                                    | 要不要 source 第一句<br>`/opt/ros/foxy/setup.bash` | 要不要 source 第二句<br>`ros2_ws/install/setup.bash` |
| ----------------------------------------------------- | -------------------------------------------- | ---------------------------------------------- |
| **只想跑官方节点**<br>如 `ros2 run demo_nodes_cpp talker`     | ✅ 必须                                         | ❌ 不需要                                          |
| **跑自己编译的节点/消息/launch**<br>如 `ros2 run my_pkg my_node` | ✅ 必须                                         | ✅ 必须                                           |
| **跑体检脚本**（它调用你自己编的 `env_check_pkg`）                   | ✅ 必须                                         | ✅ 必须                                           |
| **已经写进 `~/.bashrc`**                                  | 终端自动执行                                       | 终端自动执行                                         |

```

### 5.3 What you changed or ignored and why

Explain briefly:
- Did the AI recommend something unsafe?
- Did you modify its solution?
- Did you double-check with official docs?

**Your explanation:**  
_[Write your analysis here]_

### 5.4 Final solution you applied

Show the exact command or file edit that fixed the problem:

```bash
[Your final command/code here]
```

**Why this worked:**  
_[Brief explanation]_

---

## 6. Reflection (3–5 sentences)

Short but thoughtful:

- What did you learn about configuring robotics environments?
- What surprised you?
- What would you do differently next time (backup, partitioning, reading error logs, asking better AI questions)?
- How confident do you feel about debugging ROS/Python issues now?

**Your reflection:**

_[Have a comprehensive experience of configure the ROS2 development environment mannually due to cursors'limit]_
_[Cursor is such a powerful development platform except for a little bit expensive for me]_
_[Next time I may try something new for partitioning in computer or directly use VM ware to visualize the system, it's important to keep environment clean and easy to understand.]_ 
_[Always positive, thanks for detailed instruction like presentation and template, it's a really massive work!]_

---

## 7. Declaration

✅ **I confirm that I performed this setup myself and all screenshots/logs reflect my own environment.**

**Name:**  
_[LIU Xiaolu]_

**Student ID:**  
_[25125873G]_

**Date:**  
_[Date of submission]_

---

## Submission Checklist

Before submitting, ensure you have:

- [√] Filled in all system information
- [√] Included actual terminal outputs (not just screenshots)
- [√] Provided at least 2 screenshots (Python tests + ROS talker/listener)
- [√] Documented 2–3 real problems with solutions
- [√] Completed the AI usage section with exact prompts
- [√] Written a thoughtful reflection (3–5 sentences)
- [√] Signed the declaration

---

**End of Report**
