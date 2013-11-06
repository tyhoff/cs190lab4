# CS190 Lab 4 - Eclipse Debugging #

The purpose of this lab is for you to learn how to debug Java code in Eclipse. After this lab, you will know the basics of using breakpoints, watchpoints, and changing values during runtime.

Before starting the lab, please navigate to [the lecture material](http://courses.cs.purdue.edu/cs19000:fall13:lecture_4) and review everything of lecture 4. You can also look at [this website](http://javapapers.com/core-java/top-10-java-debugging-tips-with-eclipse/) because it mentions most of the lecture material. 

## Setup ##

Depending on your working environment, perform the appropriate action:

| Environment   | Action        |
| ------------- | ------------- |
| Linux Lab Machine            | Open a terminal window        |
| Windows or Personal Computer | SSH into `data.cs.purdue.edu`*  |

----

\* You must have X11 forwarding enabled. If you are on the Windows Lab Computer, follow the instructions below:

1. Search for 'Xming' in the start menu and run it.
2. Open PuTTy
3. Expand the 'SSH' tab from the 'Category' list
4. Choose 'X11' from 'SSH' list
5. Check 'Enable X11 Forwarding'
6. Connect like normal to `data.cs.purdue.edu` within PuTTy.

## Things To Know ##

Nothing this time around.


## Downloading and Opening the cs190lab4 Directory ##

1. Copy the Clone URL under the `HTTPS clone URL` label (right side of page).
2. In your home directory, type the terminal command, replacing `<GitHub Clone URL>` with the URL that you copied.
   
    ```bash
    git clone <GitHub Clone URL> ~/cs190lab4
    ```

3. A directory named `cs190lab4` appeared in your home directory (if that was your working directory).
4. In the same terminal, type 

    ```bash
    eclipse &
    ```
5. When Eclipse prompts you for a workspace, you can keep the default one or choose a new one.
6. Click **File**, then **Import**, expand **General**, and choose **Existing Projects Into Workspace**
7. Next to "Select a root directory:", click **Browse**
8. Find the directory named `cs190lab4` in your home directory, select it, and click **OK**

    ![*Adding Project*](http://i.imgur.com/InWhYnI.png)    

9. Click **Finish**


## Eclipse Initial Setup

1. If you see the "Welcome to Eclipse" screen, click the 'X' next to the "Welcome" tab.
2. In the top menu bar, click **Window**, then **Preferences**. 
3. In the top left of the preferences window, replace "type filter text" with "step filtering".
4. Check "Use Step Filters" if not already, and check each box. 

    ![*Setting Up Step Filters*](http://i.imgur.com/hvKgmnd.png)

## Part 1 - Watch Me ##

### What does the program do? ###
The program creates a Functions object, which contains 1000 different functions. If any of these functions return true, then `num` gets doubled. By default, the variable `num` starts at 5 and ends at 20. An example call to these functions is below.

```java
if (wm.function1()) num *= 2; else trash *= num ;
if (wm.function2()) num *= 2; else trash *= num ;
...
if (wm.function999()) num *= 2; else trash *= num ;
if (wm.function1000()) num *= 2; else trash *= num ; 


/* Explanation */

if (wm.functionX())  // wm.functionX() will return true or false

num *= 2  // will be executed if wm.functionX() returns true;

trash *= num  // will be executed if wm.functionX() returns false;
```



### What is the goal? ###
Your goal is to find out which of the 1000 functions (there is more than one) return true, and in turn, double the value of `num`. The most efficient way is to use a "Watchpoint". 

**YOU MAY NOT EDIT WATCH.JAVA**

----

### Hints ###
#### Control Flow ####

You will have to use **Step Into** and **Step Over** in this exercise.

#### To set up a Watchpoint ####

1. Set a Breakpoint.
2. Run the program in "Debug" mode.
3. View the variables in the "Outline" view (by default on right).
4. Right click on the one you want to "Watch", and select **Toggle Watchpoint**.

    ![*Setting a Watchpoint](http://i.imgur.com/QnCnvyI.png)    

5. In the "Breakpoints" view (by default top right), specify if you want to break at each access or just modifications of the variable.

    ![*Trigger on Access and/or Modification](http://i.imgur.com/q8J6BiO.png)



## Part 2 - Secret Key ##

### What does the program do? ###

Each person has a unique "Secret Key" that is tied to his/her username. There is a program called `GetKey` that will create a `KeyGenerator` object. `KeyGenerator` can correctly generate unique keys, but the original creator forgot to prompt the user for their username. Because of this, it causes an error.

### What is the goal? ####

You need to get the program to run successfully so that it prints out a unique key that is associated to your username. You can not edit the code of `KeyGenerator`, you can only debug the code. 


### How the **** do I do that? ###

A snippet of `KeyGenerator` is below. 

```java
// username of student
String username = null;
HashMachine hm = new HashMachine();
 
// produces error by default
String secret = hm.secretKey(username);
```

Notice that `username` is **null** when passed into `hm.secretKey()`. 

You must change the value of `username` to **YOUR OWN USERNAME**. We have a list of "Secret Keys" that are associated with your username, and you must get the same key. 

*Look below for how to do it.*

----

### Hints ###
#### Control Flow ####

You will have to use **Step Into** and **Step Over** in this exercise.

#### To change values of variables during runtime (do both) ####

###### Option A - Display #######

1. In the top menu bar, click **Window**, then **Show View**, then select **Other...**
2. Expand the **Debug** folder, select **Display**, and click **OK**.

    ![*Adding Display Pane*](http://i.imgur.com/ZrEOzFZ.png)

3. Set a Breakpoint.
4. Run the program in "Debug" mode.
5. In the "Display" view, write a normal Java assignemnt. *ex.* `mynum = 56;`
6. Highlight the piece of code, right-click on the code, and select **Execute**.

###### Option B - Variable View #######

1. Set a Breakpoint.
2. Run the program in "Debug" mode.
3. Give focus to the "Variables" view (by default at top right).
4. Right-click on the variable you wish to change, and select **Change Value...**
5. Type in the desired value and click **OK**

> If you are inputting a String, don't surround the String with quotes ("). They are added automatically.

## Grading ##

In a terminal, with the TA present:

1. Know the two functions that change the value of 'num' in Watch.java
2. Have the "Secret" from DebugMe.java ready.
3. Show us you know how to use the Display feature.


## End of Lab ##


*If you find any bugs within the code or misspellings in the write-up, please tell the TA. Thanks!*
