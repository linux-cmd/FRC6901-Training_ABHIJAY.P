# FRC 6901 Programming Training

This repository contains hands-on Java projects for learning FRC robot programming. Each project has its own Gradle/WPILib project and exercise instructions. Work through them in order, and write your own solutions in the project code.

## Start here

Begin with the [Project 1 Romi Drive course](Project%201%20Basic%20Romi%20Drive-Imported/README.md). It introduces Java robot code, controller inputs, simulation, and the project build one step at a time.

## Project map

| Project | Topic | Instructions |
| --- | --- | --- |
| 1 | Romi driving, controller input, and simulation | [Project 1 course](Project%201%20Basic%20Romi%20Drive-Imported/README.md) |
| 2 | Robot speed modes and a basic state machine | [Project 2](Project%202%20Basic%20State%20Machine/README.md) |
| 3 | Command-based programming | [Project 3](Project%203%20Command%20Based/README.md) |
| 4.1 | Timed autonomous, non-command-based | [Project 4.1](Project%204/Project%204.1%20Basic%20Autonomous/README.md) |
| 4.2 | Timed autonomous, command-based | [Project 4.2](Project%204/Project%204.2%20Basic%20Autonomous/README.md) |
| 5 | Closed-loop control and PID | [Project 5](Project%205%20Closed%20Loop%20Control/README.md) |

The active training projects use WPILib/GradleRIO 2026 and Java 17. The older Project 1 copy is kept in the [archive](archive/Project%201%20Basic%20Romi%20Drive%20-%20WPILib%202021/README.md) for reference; use the Project 1 course above instead.

## Setup

Install [WPILib](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html) for the season used by the projects. On Windows, follow the WPILib setup guide for installing the required FRC tools too. Each project contains its own Gradle wrapper, so run Gradle commands from that project's folder.

Open and work on one robot project at a time. Several projects contain a class named `frc.robot.Main`; opening every project as one Java workspace can make the Java tools unsure which robot program to run. The `.code-workspace` files used on the original development computer are intentionally not part of GitHub because they contain computer-specific Java paths. You can open a project folder directly in VS Code or create your own workspace file.

## Git workflow

This repository is a personal fork of the team training source. The intended remotes are:

- `origin`: your GitHub copy, where you push your work;
- `upstream`: the original team repository, where you get new training material.

For the recommended branch, review, and commit process, see [CONTRIBUTING.md](CONTRIBUTING.md). Keep commits small and focused, and check `git status` before committing. Build output, simulator state, and personal workspace files are ignored by `.gitignore`.

## References

- [WPILib documentation](https://docs.wpilib.org/en/stable/)
- [WPILib Java API](https://first.wpi.edu/wpilib/allwpilib/docs/release/java/index.html)
- [WPILib Java examples](https://github.com/wpilibsuite/allwpilib/tree/main/wpilibjExamples/src/main/java/edu/wpi/first/wpilibj/examples)
- [Team 6901 programming presentations](https://drive.google.com/drive/folders/1yjwFbbiTtUnBOTWPiMXydjgDlf6OWUSa?usp=sharing)
