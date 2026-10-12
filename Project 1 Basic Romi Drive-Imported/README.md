# Project 1 Course: Make the Romi Drive

Welcome! This is a guided lesson, not a timed test. You will learn a little, try one small step, and check what happened before moving on. The goal is to make the simulated Romi respond to your PS4 controller. I’ll explain the ideas and show you where to look, but you will write the exercise code yourself.

## What you will learn

By the end, you should understand how to:

- find the part of a robot program that runs during driver control;
- connect a controller to your Java program;
- read stick movement as numbers called axes;
- send those numbers to the provided drivetrain;
- build and test one change at a time.

## Lesson 0: Open the right project

1. In VS Code, choose **File > Open Workspace from File...**.
2. Open `FRC6901-Project-1.code-workspace`.
3. In Explorer, open `src/main/java/frc/robot/Robot.java`.
4. Confirm the terminal or Explorer shows the Project 1 folder, not the repository root or another project.

This workspace contains one robot project. That matters because every project has a class named `frc.robot.Main`; opening many projects together can confuse Java tools about which robot to start.

## Lesson 1: Take a tour of the robot code

Before changing anything, read these files:

- `Main.java` starts the robot program. You normally leave it alone.
- `Robot.java` decides what the robot does in each mode. This is where you will work.
- `RomiDrivetrain.java` controls the simulated motors and provides a ready-to-use drive method.
- `RomiGyro.java` and the simulation code help the pretend robot behave like a Romi. You do not need to edit them for this lesson.

In `Robot.java`, find `mDrivetrain` and `teleopPeriodic()`.

Vocabulary:

- A **class** is a kind of thing your program knows how to make, such as `Robot` or `XboxController`.
- An **object** is one usable instance of a class. A controller object lets your code ask what the physical controller is doing.
- A **method** is a named action. `teleopPeriodic()` is called repeatedly while the robot is in driver-control mode.
- A **field** is a variable stored by an object, so multiple methods can use it.

Learning checkpoint: In your own words, point to the method that repeats during driver control and the field that represents the drivetrain. You do not need to change code yet.

## Lesson 2: Observe the controller

1. Plug the PS4 controller into your computer with a USB cable.
2. Open the Command Palette with **Ctrl+Shift+P** and choose **WPILib: Simulate Robot Code**. If asked, choose **Sim GUI**, then **OK**.
3. In Robot Simulation, find **System Joysticks**. Your controller may be named **Wireless Controller**.
4. Drag it onto `Joystick[0]` in the **Joysticks** panel.
5. Keep the robot **Disabled**. Move one stick at a time and observe the axis values.

An **axis** is a number that changes as you move a stick. Values are usually between `-1` and `1`; the sign tells you which direction. Record which axis changes for forward/back and which changes for turning. Do not guess—the PS4 layout can differ from what you expect.

If the simulation says **Disconnected**, check the terminal. If it shows `Robot program startup complete` and the Gradle task is still running, leave it running. In the Simulation window, click **Disabled** in **Robot State**. If it remains disconnected, stop that run and launch **WPILib: Simulate Robot Code** again from this Project 1 workspace. Do not use the ordinary Run or Debug button. If it still does not work, save a screenshot of the whole simulation window and terminal.

Learning checkpoint: You should know the controller's port and the two axis numbers you plan to use. The port shown as `Joystick[0]` is port 0.

## Lesson 3: Make a controller object

Look near the top of `Robot.java` at its `import` lines. An **import** tells Java which library class you want to use. This starter file already imports `XboxController`; WPILib uses that controller class for a standard gamepad layout, including many PS4 setups. You can compare the values you observe in the simulator with the controller documentation linked below.

Your task in this lesson is to create a controller object for port 0 as a field in `Robot`, near the existing drivetrain field.

Think of the pieces this way:

- the class name says what kind of object to make;
- a variable name is how your code will refer to it;
- the port number tells WPILib which controller to read.

Use the existing `mDrivetrain` field as an example of where fields go. Use the `XboxController` import and its documentation to choose the correct constructor. Type the line yourself, save, and build before continuing.

## Lesson 4: Read stick values

Now look inside `teleopPeriodic()`. This method repeats while the robot is in Teleop, so it is the right place to read the latest stick positions and request a drive action.

For each direction you recorded:

1. Use the controller object's documentation to find the method that reads an axis.
2. Give that method the axis number you observed.
3. Store or use the returned number as the drive input.

The documentation calls these values **speed** or **axis** values. In Java, a decimal number such as `0.25` has type `double`. The drivetrain method expects two `double` values from `-1` to `1`.

## Lesson 5: Connect the inputs to the drivetrain

Open `RomiDrivetrain.java` and find `arcadeDrive`. Read its comment and method body. It already combines the two motor outputs for you:

- first value: forward or backward speed;
- second value: turn speed.

Back in `Robot.java`, use the drivetrain field to call that method from `teleopPeriodic()`, passing the two controller readings in the correct order. This is the connection you are building: controller sticks → axis readings → drivetrain method → simulated motors.

Make one small edit at a time. Save, build, and read the first error if the build fails. An error is information: Java often tells you which name, punctuation, or type it could not understand.

## Lesson 6: Build and try it

1. Open **Terminal > New Terminal**. Make sure the terminal is inside `Project 1 Basic Romi Drive-Imported`.
2. Run:

   ```powershell
   .\gradlew.bat build
   ```

3. Wait for **BUILD SUCCESSFUL**. If not, read the first error carefully, fix one issue, and build again.
4. Start **WPILib: Simulate Robot Code** from the Command Palette. Leave the simulation task running while you test.
5. Confirm the controller is assigned to `Joystick[0]`.
6. Select **Teleop** in the Robot State panel. Test one direction at a time, then release the sticks. Select **Disabled** before closing the simulator.

If a direction is reversed, use the axis values you observed to reason about the sign. Change only the relevant input, then build and test again.

## A helpful debugging routine

When something does not work, check these in order:

1. Is the correct Project 1 workspace open?
2. Did the build finish with **BUILD SUCCESSFUL**?
3. Is the simulation terminal still running and showing `Robot program startup complete`?
4. Is the controller plugged in and assigned to `Joystick[0]`?
5. Are you in **Teleop** when trying to drive?
6. Do the axis readings change when you move the sticks?
7. Does the first build error point to a name, missing symbol, or punctuation issue?

Change one thing at a time. That makes it easier to learn which change fixed—or caused—the problem.

## Review: explain it back

Try explaining these ideas aloud or in your notes:

- What does `teleopPeriodic()` do, and why do controller readings belong there?
- What is an axis, and how did you find the correct axis numbers?
- What are the two inputs to `arcadeDrive`, and in what order are they used?
- What is the difference between building the code and running the simulation?

## You have completed the lesson when...

- the project builds successfully;
- you can explain how your controller readings reach the drivetrain;
- the simulated Romi goes forward/back and turns using the controls you selected;
- releasing the sticks stops the Romi.

## Helpful references

- [WPILib XboxController documentation](https://first.wpi.edu/wpilib/allwpilib/docs/release/java/edu/wpi/first/wpilibj/XboxController.html)
- [WPILib Joystick documentation](https://first.wpi.edu/wpilib/allwpilib/docs/release/java/edu/wpi/first/wpilibj/Joystick.html)
- [WPILib simulation GUI guide](https://docs.wpilib.org/en/stable/docs/software/wpilib-tools/robot-simulation/simulation-gui.html)
- [WPILib examples](https://docs.wpilib.org/en/stable/docs/software/examples-tutorials/wpilib-examples.html)
- [Video: launching simulation](https://youtu.be/Hww2kUTNgto)
- [Video: using a keyboard as a controller](https://youtu.be/5PJP6-VLwk4)
