# Project 1: Make the Romi Drive

## What are you making?

You are going to make the little simulated robot, called the **Romi**, respond to your PS4 controller.

- Move one stick up or down to move forward or backward.
- Move another stick left or right to turn.
- Let go of the sticks to stop.

The project already has code that can move the Romi. Your job is to connect the controller to that code.

## First: open the right project

If you opened `FRC6901-Project-1.code-workspace`, look in the Explorer for **Project 1 Basic Romi Drive-Imported**. Open this file inside it:

`src/main/java/frc/robot/Robot.java`

That is the file you will edit. There are two Project 1 folders in this repository. The folder named **Project 1 Basic Romi Drive** is an older copy. Do your work in the `-Imported` folder when using the Project 1 workspace.

## Words you will see

- **Controller**: your PS4 gamepad.
- **Joystick**: another name WPILib uses for a controller connected to the computer. In the simulator, `Joystick[0]` means controller port 0.
- **Axis**: a number that changes when you move a stick. For example, pushing a stick up or down changes one axis.
- **Teleop**: the mode where a person controls the robot. It means “operator control.”
- **Drivetrain**: the motors and wheels that move the robot.
- **Arcade drive**: controlling forward/backward movement and turning with two separate numbers.
- **Method**: a named piece of code that does a job. `teleopPeriodic()` is a method that runs over and over during Teleop.
- **Build**: ask Gradle to check and compile your code. If it succeeds, your Java code has no compile errors.
- **Simulation**: a pretend robot running on your computer, so you can test without a real robot.
- **USB port number**: the number WPILib uses to identify a controller. If the simulator says `Joystick[0]`, that number is `0`.

## Part 1: make sure the controller is visible

1. Plug the PS4 controller into your computer with a USB cable.
2. In VS Code, open the Project 1 workspace by choosing **File → Open Workspace from File…** and selecting `FRC6901-Project-1.code-workspace`.
3. Open the Command Palette with **Ctrl+Shift+P**. Type `WPILib: Simulate Robot Code` and select it.
4. In the Robot Simulation window, look for **System Joysticks**. Your PS4 controller might be called **Wireless Controller**.
5. Drag **Wireless Controller** onto `Joystick[0]` in the Joysticks panel.
6. Keep the robot **Disabled** for now. Move one stick a little and watch the numbers in the Joysticks panel. Notice which number changes. Do the same with the other stick.

If the Robot Simulation window says **Disconnected**, the robot program is not connected yet. Stop the simulation and start `WPILib: Simulate Robot Code` again while the Project 1 workspace is open.

## Part 2: decide what each stick should do

Write down what you observe before coding:

| What you want the Romi to do | What you move | Which number changes? |
| --- | --- | --- |
| Go forward and backward | Move one stick up and down | Write down the axis number |
| Turn left and right | Move another stick left and right | Write down the axis number |

An **axis number** is just the number next to the changing stick value. The value may be positive in one direction and negative in the other. Use the simulator to discover which direction is which. PS4 controllers can use a different layout from Xbox controllers, so check instead of guessing.

## Part 3: connect the controller in your code

In `Robot.java`, your goal is to:

1. Make a controller object that represents the controller on port `0`.
2. In `teleopPeriodic()`, read the axis for forward/backward and the axis for turning.
3. Give those two values to the drivetrain's `arcadeDrive` method. The method wants the forward/backward value first and the turning value second.

Use the WPILib documentation below to look up how to create the controller object and read an axis. You choose the class and method names based on what you learn. Try one small change at a time and save the file.

## Part 4: check your work

1. Open the VS Code terminal: **Terminal → New Terminal**.
2. Make sure the terminal is in the `Project 1 Basic Romi Drive-Imported` folder.
3. Type this and press Enter:

   ```powershell
   .\gradlew.bat build
   ```

4. If it says **BUILD SUCCESSFUL**, start `WPILib: Simulate Robot Code` again.
5. In Robot Simulation, make sure the PS4 controller is still assigned to `Joystick[0]`.
6. In the simulated Driver Station window, select **Teleop** to let your controller drive.
7. Test one direction at a time: forward, backward, left, and right. Let go of the sticks and check that the Romi stops.
8. If a direction is backwards, change the direction of that input in your mapping and test again.
9. When finished, select **Disabled** before closing the simulator.

If the build reports an error, look at the first error message. It usually tells you which file and line needs attention. Fix that issue, save, and run the build again.

## What files should you change?

For this project, work in `Robot.java`. The other files already provide the robot startup, drivetrain, and simulation support. You do not need to edit `Main.java`, `RomiDrivetrain.java`, or `RomiGyro.java` to complete this exercise.

## How do you know you finished?

- The project builds successfully.
- The simulator connects to the robot program.
- The PS4 controller is assigned to `Joystick[0]`.
- One stick moves the Romi forward and backward.
- Another stick turns the Romi left and right.
- The Romi stops when you let go of the sticks.

## Helpful links

- [XboxController documentation](https://first.wpi.edu/wpilib/allwpilib/docs/release/java/edu/wpi/first/wpilibj/XboxController.html)
- [Joystick documentation](https://first.wpi.edu/wpilib/allwpilib/docs/release/java/edu/wpi/first/wpilibj/Joystick.html)
- [WPILib examples](https://docs.wpilib.org/en/stable/docs/software/examples-tutorials/wpilib-examples.html)
- [Video: launching simulation](https://youtu.be/Hww2kUTNgto)
- [Video: using a keyboard as a controller](https://youtu.be/5PJP6-VLwk4)
