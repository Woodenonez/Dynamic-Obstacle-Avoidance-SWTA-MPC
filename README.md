# Dynamic Obstacle Avoidance via Iterative Prediction (SWTA) and Control (MPC)
This repository contains the code to execute the simulated system for predictive dynamic obstacle avoidance based on multimodal motion prediction and model predictive control in Python. The corresponding explanation of the algorithm can be found in the paper [Prescient Collision-Free Navigation of Mobile Robots With Iterative Multimodal Motion Prediction of Dynamic Obstacles](https://ieeexplore.ieee.org/document/10185133). This paper explores safer interactions between mobile robots and dynamic obstacles and presents a comprehensive approach to collision-free navigation in indoor environments.


![Example](doc/cover.png "Example")

## Quick Start
The major interface is introduced in "doc/interface.pdf".

### 1. OpEn
The NMPC formulation is solved using open source implementation of PANOC, namely [OpEn](https://alphaville.github.io/optimization-engine/). Follow the [installation instructions](https://alphaville.github.io/optimization-engine/docs/installation) before proceeding. 

### 2. Install dependencies
It is suggested to use a virtual environment. After activating the virtual environment, install the dependencies:
```
pip install -r requirements.txt
```

### 3. Generate MPC solver
Go to "solver_build.py", use the proper configuration name **cfg_fname** and run
```
python solver_build.py
```
After this, a new directory *mpc_solver* will appear and contain the solver.

### 4. GPU acceleration
The motion prediction part is accelerated by GPU. Make sure you have the correct driver and CUDA installed. This is checked in the *main.py* (by printing out *GPU available: True*). For Ubuntu, the driver can be installed via the *ubuntu-drivers*.

## Use Case
Run *main.py* for the warehouse simulation (one robot, one or more pedestrians) in Python. The evaluation is in *main_eva.py*, which compares the situation with and without the motion prediction part.

To run other cases or create your own cases, go to *main_base* and create scenarios based on the examples. Make sure to modify the **SCENARIO_NUM**:
``` Python
class MainBase:

    HUMAN_SIZE = 0.2
    HUMAN_VMAX = 1.5
    HUMAN_STAGGER = 0.5

    SCENARIO_NUM = XXX # modify this
    HUMAN_STARTS, HUMAN_PATHS, ROBOT_START_POINT, ROBOT_PATH = scenario(SCENARIO_NUM)
```




