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
    3. (Step 12) Function fail: fail to send email regarding all expenses history.

We will describe the two challenges in the next section.

## Challenges
### <font color=LightCoral>1. Environment Problem</font>

<font color=red>For macOS, we encountered difficulties installing the specified version of matplotlib (i.e., version 3.4.3). Consequently, we opted to install the latest version of matplotlib. However, during the execution of bot.py, any invocation of the matplotlib library led to a program crash. To address this issue, we changed the backend type of the matplotlib library to 'Agg'. This adjustment enabled smooth execution of the program on macOS.</font>

### <font color=LightCoral>2. Running Problem</font>

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

### <font color=LightCoral>3. Function fail</font>

After selecting /sendEmail from the function menu and input the destination email address, the whole program stop to run as it fails to login an gmail account due to the following reason.

     From May 30, 2022, ​​Google no longer supports the use of third-party apps or devices to sign 
     in to your Google Account using only your username and password.

To solve this problem, user need to generate new-app-password for mail access in google security setting. The password will be generated for the, then user can use this password in gmail_password function in Python.

After following the above procedure with a new created google account for sending emails, this problem is solved with success.

## How to Avoid Pain

The environment problem we met probably comes from not testing the project on both Windows and macOS system.

The running problem we met probably comes from not testing the project for all data file. The author may only test some of the data in the project, then push all other data to GitHub.It is necessary to check the codes can run on all the data. Then it is the time to release all the data and codes. We will check this rubric seriously during the **Project 2** to avoid this problem.
