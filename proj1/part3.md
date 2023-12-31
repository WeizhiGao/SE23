# Part 3: diffculties in running process

## Overview
The project we choose is **Slashbot** ([Link](https://github.com/secheaper/slashbot)). It is a Telegram Bot that assists users in recording daily expenses on a local system.

There are mainly five steps to deploy and run the **Slashbot**: 

    1. Install a python environment for running the project
    2. Install Telegram desktop application and login in
    3. Create a bot by BotFather and get the api token for python
    4. Run a python file in Terminal
    5. Use functions from the /menu to make operations on expenses.

After these five steps, we can use the **Slashbot**. However, there were three main problem while deploying **Slashbot**: 

    1. (Step 1) Environment Problem: fail to install the python environment according to the requirements.txt file in macOS system
    2. (Step 4) Running Problem: fail to run bot.py file
    3. (Step 5) Function fail: fail to send email regarding all expenses history.

We will describe the three challenges in the next section.

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

To solve this problem, user need to generate new-app-password for mail access in google security setting. The password will be generated by the system for the user after enabling the 2-step verification, then user can use the generated new-app-password in gmail_password function in Python to login.

After following the above procedure with a new created google account for sending emails, this problem is solved with success.

## How to Avoid Pain in Future

The environment problem we met probably comes from not testing the project on both Windows and macOS system. For future development, we will clearly document any differences in setup, installation, or usage between the platforms. In addition, If our program requires external software or libraries, we will ensure that they are available for both macOS and Windows. Actively seeking cross-platform libraries or tools as our primary choices. Besides, we may regularly updating our dependency lists, so users are always informed about the required software versions and potential compatibility issues.

The issue we encountered during execution likely stems from an incomplete testing scope concerning the data files. It appears that the original author may have tested the codes using only a subset of the available data before committing the entirety of the files, including those untested, to the GitHub repository. This approach can introduce unforeseen challenges, especially when the untested data has unique characteristics or anomalies that the code isn't equipped to handle. As we progress into Project 2, our team is committed to diligently following the stipulated rubric. This ensures that we not only meet the baseline expectations but also preemptively address any potential issues.

Besides, to ensure that other developers can run your program in the future, even if certain settings or dependencies change. We will ensure that our code has comprehensive error handling. Instead of vague error messages reported automitically by the system, we will provide detailed ones that explain what went wrong and possibly how to fix it.
