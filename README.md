# Research Track 2 assignment - Robotics Engineering
## Control of a robot in a simulated environment (Jupyter Notebook)
### Author: Simone Contorno

<br>

### Introduction
An overview of this program.<br>
[Go to Introduction](#intro)

### How it works
A rapid description of how the program works (pseudo-code).<br>
[Go to How it works](#how)

### Installation and Execution
How install and run this program in Linux.<br>
[Go to Installation and Execution](#installation)

### Improvements
How Jupyter Notebook interface could be improved.<br>
[Go to Improvements](#improve)

<a name="intro"></a>
### Introduction

The main aim of this repository is provide an alternative, more modular, implementation of the program that can be downloaded at this link:<br>
https://github.com/simone-contorno/rt-assignment-3<br>

Now, the User Interface, wrote in python, is implemented in a different node and also in Jupyter. <br>
Additionally, in Jupyter, it is possible to plot:
<ul>
    <li>the robot position (with and without tracking all the history position);</li>
    <li>the laser scanner data;</li> 
    <li>the number of reached and non-reached goals.</li>
</ul>
These can be plot directly by the UI (discouraged, read the Improvements section), or using a dedicated cell (penultimate one).<br>
It is also possible visualize the 3D map of Rviz running the last cell.

<a name="how"></a>
### How it works

Read the README.md file at: https://github.com/simone-contorno/rt-assignment-3.

<a name="installation"></a>
### Installation and Execution

Download this repository:

<pre><code>git clone https://github.com/simone-contorno/rt2-assignment</code></pre>

Copy or move the folder rt2_robot into the src folder of your ROS workspace.<br> 
Go into the root folder of your ROS workspace and build the workspace: 

<pre><code>catkin_make</code></pre>

Afterwards refresh the package list:

<pre><code>rospack profile</code></pre>

Now, to launch all these nodes using the launch file final_assignment.launch, install xterm: 

<pre><code>sudo apt install xterm</code></pre>

Launch the launch file:

<pre><code>roslaunch rt2_robot rt2_robot.launch</code></pre>

Alternatively, if you don't want intall xterm, you can open 4 terminals and:
<ul> 
    <li>In the first one launch the environment:
        <pre><code>roslaunch rt2_robot simulation_gmapping.launch</code></pre>
    </li>
    <li>In the second one launch the action server move_base:
        <pre><code>roslaunch rt2_robot move_base.launch</code></pre>
    </li>
    <li>In the third one run the logic of the robot:
        <pre><code>rosrun rt2_robot rt2_robot_logic</code></pre>
    </li>
    <li>In the fouth one run the user interface:
        <pre><code>rosrun rt2_robot rt2_robot_interface.py</code></pre>
    </li>
</ul>

In this second case, be careful to run the rt2_robot_logic before starting to use the user interface, otherwise you can encounter some troubles!<br>

If you want to use the Jupyter Notebook interface, you need to start it:

<pre><code>jupyter notebook --allow-root --ip 0.0.0.0</code></pre>

Now you can access to the rt2_robot folder in your ROS workspace and open the file rt2_robot_jupyter_ui.ipynb.
Once open, run all the cells except for the penultimate and the last one (they have a specific function, read the comments to know more about it); in the cell with the interface function you will find the buttons to control the robot.

<a name="improve"></a>
### Improvements

In Jupyter Notebook, when data are plotted the kernel remains busy and it cannot be possible continue to use the interfice until the plotting windows will be closed. Then, a good improvement whould be allow to the user to continue to use the interface while it is plotting the data.
