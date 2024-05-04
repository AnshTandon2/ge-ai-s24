# GE Research GE:AI - Project

## Technologies Used
- Open AI Gymnasium
- MuJoCo 
- Gazebo3D
- RoboHive


## Supported Platforms
- Ubuntu
- Windows
    - Must use [WSL](https://docs.microsoft.com/en-us/windows/wsl) (Windows Subsystem for Linux)
- MacOS

## Video Demonstration

![Demo](https://private-user-images.githubusercontent.com/43502767/327970852-e44f894d-d630-4294-8650-445774f78c5e.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTQ4NTE4MTMsIm5iZiI6MTcxNDg1MTUxMywicGF0aCI6Ii80MzUwMjc2Ny8zMjc5NzA4NTItZTQ0Zjg5NGQtZDYzMC00Mjk0LTg2NTAtNDQ1Nzc0Zjc4YzVlLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDA1MDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwNTA0VDE5MzgzM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTAxZTc5YjM3ZTdkMWVhMDBkMjQyZmI1MGNlZDZlYTljZGEwNTEzZThjMzE4MzMzYjU0M2I1ZDgyYmM5MWI1MzImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.zjkZexubx9UjDGUnyh2kEdY1ccZ3gKvikbWxyhdTFhg)


## Preliminary Steps
1. Install MuJoCo and pyenv (python version management)
- [Install Mujoco](https://mujoco.readthedocs.io/en/stable/programming/index.html#getting-started)
- Install pyenv

Linux/WSL:
```
sudo apt update
sudo apt-get install -y build-essential zlib1g-dev libffi-dev libssl-dev liblzma-dev libbz2-dev libreadline-dev libsqlite3-dev
curl https://pyenv.run | bash
echo -e 'export PATH="$HOME/.pyenv/bin:$PATH"\neval "$(pyenv init --path)"\neval "$(pyenv init -)"\neval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
source ~/.bashrc
```
> NOTE: echo command adds pyenv to .bashrc to start it every time you open a terminal

MacOS:
```
brew install pyenv
brew install pyenv-virtualenv
```
2. Install known working version of python
```
pyenv install 3.9.18
```

3. Clone repo 

```
git clone https://github.com/purdue-mars/VIP-GEAI
cd 02-block-pick-and-place
```

4. Create virtual environemnt, install repo, and dependencies 

```
pyenv virtualenv 3.9.18 pick_n_place 
pyenv activate pick_n_place
pip3 install -e .
```

## Part 1: Open-loop Box Pick and Place

Goal: get the robot to pick up the brick in the right bin and place it in the left bin within the **target green zone** via following a precomputed trajectory open-loop

To run the starter script:
``` 
cd pick_n_place
python3 part_1/main.py 
```
> NOTE: Initially, the robot will just go to the **target green zone**

Update the `part_1/main.py` file with the following steps:
1. STEP 1.1: Generate Task-relevant Poses
2. STEP 1.2: Create Joint-position trajectory following the task-relevant poses

### Helpful tips

- On the left sidebar of the MuJoCo Renderer, click: 
  - `Rendering > Frame > Site|Body|Geom` to toggle rendering of the coordinate frames
  - `Rendering > Label > Site|Body|Geom` to toggle rendering of the labels
- Helpful utils are provided for you to in the robohive library:
  - [quat2mat](https://github.com/vikashplus/robohive/blob/ef6f2c3deb93555d779bb3f9af0b3c21414c6bc0/robohive/utils/quat_math.py#L152): convert quaternion to rotation matrix
  - [mat2quat](https://github.com/vikashplus/robohive/blob/ef6f2c3deb93555d779bb3f9af0b3c21414c6bc0/robohive/utils/quat_math.py#L110): convert rotation matrix to quaternion
  - [generate_joint_space_min_jerk](https://github.com/vikashplus/robohive/blob/ef6f2c3deb93555d779bb3f9af0b3c21414c6bc0/robohive/utils/min_jerk.py#L5): generate joint space trajectory given start and end joint angles

## Part 2: Box Pick and Place with Collision Avoidance

Coming soon

## Part 3: Closed-loop Box Pick and Place using Vision and Learning

Coming soon
