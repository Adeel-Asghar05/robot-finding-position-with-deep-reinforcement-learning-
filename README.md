🦾 Robot Navigation with PyBullet + PPO

This project implements a custom robot navigation environment in PyBullet
 and trains it using Proximal Policy Optimization (PPO) from Stable-Baselines3
.

The robot (defined in ryres.urdf) learns to navigate towards random goal positions using reinforcement learning.

📂 Project Structure
├── robot_env.py        # Main Python code (environment + training + testing)
├── ryres.urdf          # Custom robot model (URDF format)
├── meshe/              # STL mesh files for robot parts (used in URDF)
└── README.md           # Project documentation

⚙️ Features

✅ Custom Gymnasium Environment (RobotEnv)

✅ PyBullet physics simulation with gravity & collision

✅ Discrete action space (Forward, Left, Right)

✅ Reward shaping:

Distance progress reward

Heading alignment reward

Turning penalty/bonus

✅ Custom callback (EpisodeTracker) for episode tracking

✅ Training with PPO (Stable-Baselines3)

✅ URDF robot model (ryres.urdf) with wheels, arms, and grippers

🤖 Robot Model (URDF)

The robot is defined in ryres.urdf, which contains:

Base link

Wheels (drive + support wheels)

Arms & grippers

Meshes (STL files in meshe/ directory)

PyBullet loads this URDF to simulate physics, dynamics, and collisions.

📊 Training Rewards

The agent receives:

+10 × distance progress

+0.5 × cos(heading error) (alignment bonus)

+0.3 for purposeful turns (if they reduce heading error)

-0.045 per step (time penalty)

+100 for reaching the goal

-50 if maximum steps reached
