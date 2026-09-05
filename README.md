# 6-Motor Power Distribution Gearbox System

> One of the most ambitious and mechanically complex robots I have designed during my VEX Robotics career. This robot uses a combination of pneumatic clutches, a two-speed transmission, gear trains, and chain drives to dynamically redistribute motor power between three separate subsystems while simultaneously changing the drivetrain's gear ratio.

---

## Robot Design and Development

This robot was designed for the **VEX Robotics Competition (VRC) Push Back** game. The main goal of the design was to create a robot that could quickly switch between different configurations depending on what was happening during a match.

Rather than dedicating a fixed number of motors to each mechanism, I designed a system that could **redirect motor power between the drivetrain, intake, and flywheel**. Pneumatic clutches physically move gears into and out of engagement, allowing the same motors to serve different purposes.

The result is a robot that can prioritize:

- **Maximum driving speed**
- **General-purpose driving and intake**
- **Flywheel and scoring power**
- **High-torque defensive driving**

---

# 1. Design Evolution and Game Strategy

One of the biggest changes from my previous robot came from studying how the game was actually being played.

There are two **Long Goals** on the field. In the center of each Long Goal is a **Goal Control Zone**, which can hold three balls. Controlling this zone gives additional points, making it an important strategic objective.

My original robot relied heavily on **winging** — using a mechanism to move balls out of the Long Goal. However, as the game evolved, teams became better at keeping the center of the goal clear. This made winging much less effective.

If I was losing the match and the opponent controlled the center, my V1 robot had to first score enough balls to reach the center and then use the wing to clear the zone.

I wanted V2 to have a way to attack the control zone **without physically needing to reach it first**.

### The Newton's Cradle Strategy

My solution was to use a **flywheel** to shoot a ball directly into the center of the Long Goal.

The idea is similar to a **Newton's cradle**. When the launched ball enters the group of balls in the control zone, its momentum can transfer through the group and cause the ball on the opposite side to be knocked out of the zone.

This means the robot can potentially disrupt the opponent's control of the zone from a distance.

---

# 2. Early V2 Design Concepts

These were some of my early sketches for V2. I used these concepts to explore the overall layout, motor placement, intake geometry, and scoring mechanisms before building the final robot.

<div align="center">

<img src="https://github.com/user-attachments/assets/0ce3e39d-30e9-4f99-b411-dc54e31a6736" width="300">

<img src="https://github.com/user-attachments/assets/dad5ecb6-376f-41d8-9cac-937d451bd5dd" width="300">

<img src="https://github.com/user-attachments/assets/ff84876d-6cea-4f78-b8c7-db2a77808d86" width="300">

</div>

---

# 3. Motor Allocation and Power Sharing

The robot uses **eight motors total**. Instead of permanently assigning every motor to one subsystem, I designed a mechanical system that allows several motors to be redirected depending on the robot's current configuration.

The robot can operate in several important states:

| Configuration | Drivetrain | Intake / Flywheel | Purpose |
|---|---:|---:|---|
| High-Speed Drive | 8 motors | 0 | Maximum driving speed |
| General Driving | 6 motors | 2 | Normal driving while maintaining intake capability |
| Scoring / Flywheel | 4 motors | 4 | Maximum mechanism power |
| Defensive Drive | 6 motors | 2 | High-torque defensive configuration |

Two pneumatic pistons control the motor-sharing system.

### Piston A

Piston A moves a set of gears between two positions.

When extended:

- Two additional motors are connected to the drivetrain.
- The drivetrain enters the **600 RPM high-speed ratio**.

When retracted:

- Those two motors are redirected away from the drivetrain.
- Their power can be used by the flywheel system.
- The drivetrain changes to the **200 RPM high-torque ratio**.

This means one pneumatic action simultaneously changes both **motor allocation** and **drivetrain gearing**.

### Piston B

Piston B controls another pair of motors.

When extended, those motors provide additional power to the chassis.

When retracted, they are redirected to the **first and second stages of the intake**.

The flywheel is controlled separately from these intake stages.

---

# 4. Drivetrain Speed and Torque Problem

One of the main engineering problems I encountered was balancing **speed and pushing power**.

The robot uses **2.75-inch wheels**. I initially wanted the robot to have a very fast drivetrain, but the number of motors powering the drivetrain changes depending on the robot's configuration.

Four motors do not provide enough pushing power for the robot to reliably defend against another robot.

However, eight motors provide plenty of power, and six motors are still effective for normal driving.

This created a problem:

> How could I have a fast drivetrain when I needed it, but still have enough torque when I was using motors for scoring mechanisms?

The solution was a **two-speed transmission combined with the motor-sharing system**.

---

# 5. Two-Speed Transmission

The drivetrain has two gear ratios:

- **600 RPM:** High-speed driving
- **200 RPM:** High-torque driving

These values represent the speed of the drivetrain **after gearing**, rather than the nominal speed of the motors themselves.

The transmission uses a sliding gear mechanism that physically moves a gear into a different position.

<div align="center">

<img src="https://github.com/user-attachments/assets/3ba639a0-098d-420d-9bfb-641e5098cbd4" width="450">

<img src="https://github.com/user-attachments/assets/e69ff543-e6b7-4d5d-8dd1-4bb06be223cf" width="300">

</div>

The first image shows the chassis and the two gear trains used for the different drivetrain ratios.

The second shows the sliding carriage that moves the gear and changes the drivetrain ratio.

The faster ratio is useful when the robot has enough motors powering the drivetrain. When fewer motors are being used for driving, the slower ratio provides significantly more torque.

---

# 6. Mechanical Motor-Sharing System

The most complicated part of the robot is the system that physically redirects motor power.

Instead of electronically changing which mechanism a motor powers, I used **pneumatic clutches** to mechanically engage and disengage different gear trains.

There are two pneumatic clutches that allow motor power to be redistributed between the drivetrain, intake, and flywheel systems.

<div align="center">

<img src="https://github.com/user-attachments/assets/f8ce13d7-89ce-4452-8ba4-38801e178507" width="400">

<img src="https://github.com/user-attachments/assets/84457bd7-cdbb-4e13-b3da-d0b2fe4dae85" width="300">

</div>

The top view shows the two clutches used to transfer motor power between the different subsystems.

The sketch shows how one piston can activate both the clutch and the transmission.

The motors themselves do **not** move. Instead, the gears move into different positions so that the motor's power is redirected.

This approach allowed me to package multiple functions into the same physical space while avoiding the weight and space requirements of simply adding more motors.

---

## Chain Power Transfer

Some of the mechanisms were separated by too much distance to connect directly with gears.

To transfer power across these larger distances, I used a **sprocket and chain system**.

<div align="center">

<img src="https://github.com/user-attachments/assets/f362eb9f-fed3-469a-b981-ec1b48c03f9d" width="350">

<img src="https://github.com/user-attachments/assets/4df69bf1-1443-488b-91c9-2255c24b680b" width="350">

</div>

The first image shows the sprocket and chain system used to transfer power.

The second shows the beveled gears used as part of the transmission.

---

# 7. Intake and Wing Design

The intake needed to satisfy several requirements based on my strategy.

I wanted:

- A **vertical wing**
- The ability to drive underneath the Long Goal
- A compact mechanism
- A wing with a relatively small range of motion
- Precise placement inside the goal

The final design uses a **parallel four-bar linkage**.

A parallel four-bar is a linkage where the mounted mechanism maintains approximately the same orientation as it moves. In this case, the wing remains vertical relative to the floor throughout its movement.

This was especially useful because I needed the wing to remain perpendicular to the floor while keeping the overall mechanism compact.

---

# 8. Four-Bar Mechanism

The four-bar mechanism went through several iterations before reaching its final design.

<div align="center">

<img src="https://github.com/user-attachments/assets/951a2255-c919-407d-8664-7df89594b5e9" width="350">

<img src="https://github.com/user-attachments/assets/90e80fd0-cf7d-49cc-8f6e-e787f0387127" width="350">

</div>

The four-bar is actuated by **two pneumatic pistons**.

The pistons push an **over-center linkage**. Once the linkage passes its center point, it mechanically locks into position.

This means the pistons do not need to continuously apply force just to hold the wing up. The linkage itself holds the mechanism in position.

---

# 9. Chassis Architecture

The motor placement required a significant departure from a typical VEX drivetrain.

Normally, drivetrain motors are mounted within the chassis rails. Because of the motor-sharing system, I needed the motors to be positioned higher and next to one another.

<div align="center">

<img src="https://github.com/user-attachments/assets/f261bbe0-8719-4142-97cf-cd39a332b317" width="450">

</div>

This unusual motor placement created additional packaging challenges because I had to fit the transmission, clutches, intake, and other mechanisms around the motors.

The final design uses the limited space inside the robot very efficiently.

---

# 10. Intake Development

The intake was designed as multiple stages that move game elements from the front of the robot toward the scoring mechanism.

A small arm at the front manipulates the game elements and feeds them into the rest of the intake.

<div align="center">

<img src="https://github.com/user-attachments/assets/3516ad72-3f51-4269-8f1f-f887541e04b5" width="300">

<img src="https://github.com/user-attachments/assets/55170800-4c27-43e2-9e45-18f21c5f980f" width="300">

<img src="https://github.com/user-attachments/assets/cd7d7d56-4bcf-4ad4-a26b-40be98e935f1" width="300">

</div>

The intake was designed around the available space created by the drivetrain and motor-sharing system.

---

## Intake Stages Installed

These images show the first two intake stages mounted to the robot.

<div align="center">

<img src="https://github.com/user-attachments/assets/264850cc-c773-412e-949b-691faf843fd5" width="300">

<img src="https://github.com/user-attachments/assets/5096daa0-a9e7-4aad-9409-381ec9920b1f" width="300">

<img src="https://github.com/user-attachments/assets/8de26fd9-d26b-41e4-9a94-668a9b9d36c5" width="300">

</div>

The different views show the relationship between the intake stages and the four-bar mechanism.

---

# 11. Ball Storage System

At the front of the robot is a **large basket** that acts as a reserve for balls.

Instead of immediately sending every ball through the scoring system, the robot can collect and store balls in the basket and score them later.

The balls are fed **upward from the bottom** of the robot.

This was a major change from V1, where the balls entered from the top and were essentially tossed into the robot.

The new system gives much more control over how the balls are stored and fed into the scoring mechanism.

---

# 12. Weight Reduction and Custom Parts

Because the robot contained a large number of mechanisms, keeping the overall weight under control was important.

One of the smaller but useful weight-saving changes was replacing standard VEX shaft collars with custom plastic versions.

<div align="center">

<img src="https://github.com/user-attachments/assets/20fefcde-33f0-46e6-af50-c1f2a22f3413" width="350">

<img src="https://github.com/user-attachments/assets/8c86951e-ea83-42f1-b918-ac675b2c2f75" width="350">

</div>

The first image compares a standard VEX shaft collar with my custom plastic version.

The second shows the **3D-printed jig** I designed to manufacture the plastic shaft collars consistently.

Small weight savings like this become valuable when they are repeated across many components.

---

# 13. Complete Robot Assembly

The final robot combines all of these systems into one compact mechanism:

- Eight total motors
- Two pneumatic power-distribution clutches
- Two-speed drivetrain
- 2.75-inch wheels
- Multi-stage intake
- Vertical wing
- Parallel four-bar linkage
- Flywheel scoring system
- Chain-driven power transfer
- Multiple gear trains
- Large front ball-storage basket

The goal was not simply to build a robot with powerful individual mechanisms. The goal was to make all of the systems work together while allowing the robot to change its priorities during a match.

---

# 14. Testing

One of the most important parts of development was testing the different drivetrain configurations in real match-like situations.

The robot's defensive configuration allows it to prioritize torque over speed.

This configuration uses the slower **200 RPM drivetrain ratio** and provides six motors to the drivetrain, giving the robot substantially more pushing capability than the four-motor configuration.

### Defensive Driving Test

[![Robot driving in defensive mode](https://img.youtube.com/vi/C5uM0KIjCk0/hqdefault.jpg)](https://youtube.com/shorts/C5uM0KIjCk0?feature=share)

---

# 15. Previous Robot: V1 Development

Before designing V2, I built V1 earlier in the same season.

V1 taught me a lot about the game, but it also exposed several limitations that directly influenced the V2 design.

<div align="center">

<img src="https://github.com/user-attachments/assets/54f4748f-9ace-4621-84a7-013075337325" width="350">

<img src="https://github.com/user-attachments/assets/7c582b40-9d73-449b-b7de-50eedddcd214" width="350">

</div>

These were some of the early V1 sketches.

---

# 16. V1 Ball Routing System

One of the most complicated mechanisms on V1 was the hood.

The hood used **three separate pneumatic pistons** to determine where a ball would go.

This created **four different possible ball paths**.

The system gave me a lot of control over ball routing, but it was mechanically complicated and required a large amount of space.

<div align="center">

<img src="https://github.com/user-attachments/assets/e860afbd-da1b-4683-bd47-85d5f88176ef" width="300">

<img src="https://github.com/user-attachments/assets/215d4b5e-5108-4932-8ff4-c75e0347bb4b" width="300">

<img src="https://github.com/user-attachments/assets/33f03e8f-628c-44df-b108-cfb477bb0f14" width="300">

</div>

### V1 Intake and Hood Test

[![V1 intake with hood](https://img.youtube.com/vi/9tBNqNpJNY4/hqdefault.jpg)](https://youtube.com/shorts/9tBNqNpJNY4?feature)

---

# 17. V1 Expandable Ramp

V1 also used an expandable ramp for game elements.

The distance a game element needed to travel changed depending on whether the hood was raised or lowered, so the ramp needed to change its effective length.

<div align="center">

<img src="https://github.com/user-attachments/assets/ac7e817c-5c12-4226-b961-18bd81ed634f" width="350">

<img src="https://github.com/user-attachments/assets/728b82bf-0c6b-48d7-979e-d001482723f3" width="350">

</div>

The first image shows the back of the V1 robot, while the second shows the expandable ramp mechanism.

---

# 18. Design Iteration and Engineering Lessons

The biggest lesson from this robot was that **mechanical complexity can be worthwhile when it directly solves a strategic problem**.

Instead of simply adding more motors, I designed a system that could change how the existing motors were used.

The final design combines:

- Mechanical power distribution
- Pneumatic clutches
- A two-speed transmission
- Gear trains
- Chain drives
- A multi-stage intake
- A parallel four-bar
- A flywheel
- Custom 3D-printed components

The most important part of the design was not any individual mechanism. It was the way the mechanisms interacted.

The robot could change from a fast drivetrain to a high-torque defensive configuration or redirect motor power toward scoring mechanisms depending on what the match required.

This design process reinforced an important engineering principle for me:

> **A good robot is not just a collection of good mechanisms. It is a system where each mechanism is designed around the others.**
```
