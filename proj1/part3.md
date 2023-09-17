# Part 3: diffculties in running process

## Overview
The project we choose is **Slashbot** ([Link](https://github.com/secheaper/slashbot)). It is a Telegram Bot that assists users in recording daily expenses on a local system.

There are mainly four steps to deploy the **Slashbot**: 

    1. Install a python environment for running the project
    2. Install Telegram desktop application and login in
    3. Create a bot by BotFather and get the api token for python
    4. Run a python file in Terminal

After these four steps, we can use the **Slashbot**. However, there were two main problem while deploying **Slashbot**: 

    1. (Step 1) Environment Problem: fail to install the python environment according to the requirements.txt file in macOS system
    2. (Step 4) Running Problem: fail to run bot.py file

We will describe the two challenges in the next section.

## Challenges
### <font color=LightCoral>Environment Problem</font>

<font color=red>TBD</font>

### <font color=LightCoral>Running Problem</font>

After setting the first 3 steps well, we need to run **bot.py** in **/src** directory. However, there are some bugs in this step.

If we do like the tutorial of setting **Slashbot**, run the following code in the root directory of the project: 

    python src/bot.py

The following error arises: 

    ModuleNotFoundError: No module named 'src'

After checking bot.py, we found it is because the function **pickle** did not find **src** module while unpickling.

To solve this problem, we change the directory of the project, and import as described in the pickle file. In this way, we change another pickle and satisty all the requiements for the unpickling operation. The command and directory is shown as follows: 

Command: 

    cd ./src
    python bot.py

Directory Tree: 

    --slashbot
        --...
        --src
            --data
            --code
                __init__.py
                user.py
            bot.py

In this way, we successfully run the project.

## How to Avoid Pain

The environment problem we met probably comes from not testing the project on both Windows and macOS system.

The running problem we met probably comes from not testing the project for all data file. The author may only test some of the data in the project, then push all other data to GitHub.It is necessary to check the codes can run on all the data. Then it is the time to release all the data and codes. We will check this rubric seriously during the **Project 2** to avoid this problem.
