# 6-Motor Power Distribution Gearbox System

> One of the most ambitious and mechanically complex robots I have designed during my VEX Robotics career. This robot uses a combination of pneumatic clutches, a two-speed transmission, gear trains, and chain drives to dynamically redistribute motor power between three separate subsystems while simultaneously changing the drivetrain's gear ratio.

---

## Robot Design and Development

This robot was designed for the **VEX Robotics Competition game Push Back**. The main goal of the design was to create a robot that could quickly adapt between driving, intake, scoring, and defensive roles without requiring a completely separate mechanism for each task.

The most important part of the design is the **power distribution system**. Instead of permanently assigning every motor to one subsystem, pneumatic clutches allow motors to be transferred between the drivetrain, intake, and flywheel.

This allowed me to build a robot that could change its mechanical configuration during a match depending on what was needed.

---

## 1. Design Evolution and Game Strategy

One of the biggest strategic problems I noticed during the season was how the game was evolving.

There are **two Long Goals** on the field. In the center of each Long Goal is a **Goal Control Zone**. The zone can hold three balls, and controlling it provides additional points.

My original robot, V1, relied heavily on **winging** — using a mechanical wing to move balls out of the Long Goal. This worked well early in the season, when there were usually several balls sitting in the goal.

However, as the meta developed, fewer balls were being left in the control zone. This made winging much less effective.

If I was behind in points and the opponent controlled the Goal Control Zone, V1 had to first score enough balls to reach the middle of the goal and then use the wing to remove the opponent's balls.

I wanted V2 to solve this problem differently.

### Using the Flywheel to Disrupt the Control Zone

Instead of physically reaching the balls with a wing, I designed the robot to shoot a ball directly into the center of the Long Goal.

The launched ball has enough momentum to disturb the group of balls sitting in the Goal Control Zone.

The idea is similar to a **Newton's cradle**. A ball entering one side of a tightly packed group can transfer momentum through the group and cause the ball on the opposite side to move.

In the best-case scenario, my launched ball enters the control zone and causes one of the opponent's balls at the other end to get knocked out of the zone.

This gives the robot a way to disrupt control **without first having to physically reach the center of the goal**.

---

## 2. Early V2 Design Concepts

These are some of the early sketches and concepts for the V2 robot.

<img src="https://github.com/user-attachments/assets/0ce3e39d-30e9-4f99-b411-dc54e31a6736" width="66%">

<img src="https://github.com/user-attachments/assets/dad5ecb6-376f-41d8-9cac-937d451bd5dd" width="66%">

<img src="https://github.com/user-attachments/assets/ff84876d-6cea-4f78-b8c7-db2a77808d86" width="66%">

These sketches helped establish the overall layout of the robot and how the drivetrain, intake, wing, and scoring mechanisms would fit together.

A major constraint was that the robot needed to be able to **drive underneath the Long Goal**. This influenced the placement and motion of the wing as well as the overall height of the robot.

---

## 3. Motor Allocation and Power Sharing

The robot uses **eight motors total**.

The key idea was to avoid permanently dedicating all eight motors to the drivetrain. Instead, pneumatic clutches allow motor power to be redistributed depending on the robot's current task.

The robot can operate in several different configurations:

| Configuration | Drivetrain Motors | Intake / Flywheel Motors | Purpose |
|---|---:|---:|---|
| High-Speed Drive | 8 | 0 | Maximum driving speed |
| General Driving | 6 | 2 | Balanced driving and intake |
| Flywheel / Scoring | 4 | 4 | Maximum scoring power |
| Defensive / High-Torque | 6 | 2 | More drivetrain torque |

The motors themselves do **not** physically move.

Instead, pneumatic pistons move gears into or out of mesh. This redirects the power coming from the motors to different mechanical systems.

This is what makes the system function like a mechanical power distribution gearbox.

---

## 4. Drivetrain Speed and Torque Problem

The drivetrain uses **2.75-inch wheels**.

One of the biggest engineering challenges was balancing speed and pushing power.

With eight motors driving the robot, a **600 RPM drivetrain ratio** provided the speed I wanted.

However, running only four motors through the same ratio did not provide enough torque for defensive situations.

Four motors simply did not have enough pushing power to reliably defend against another robot.

This created a problem:

> How could I get the speed of the 600 RPM drivetrain when I had enough motors available, but still have enough torque when only four drivetrain motors were being used?

The solution was a **two-speed transmission**.

---

## 5. Two-Speed Transmission

The drivetrain has two gear ratios:

- **600 RPM:** high-speed configuration
- **200 RPM:** high-torque configuration

These values refer to the **speed after the drivetrain gearing**, rather than the nominal speed of the motors themselves.

The high-speed ratio is useful when the robot has eight motors available for driving.

The lower-speed ratio provides much more torque and is used when fewer motors are powering the drivetrain.

<img src="https://github.com/user-attachments/assets/3ba639a0-098d-420d-9bfb-641e5098cbd4" width="66%">

The chassis contains two separate gear trains on each side. One provides the faster driving ratio, while the other provides the slower, more powerful ratio.

---

## 6. Mechanical Motor-Sharing System

The power distribution system uses **two pneumatic clutches**.

A pneumatic clutch is a mechanism that uses a piston to physically move gears into or out of engagement. This allows a motor to transfer its power between different mechanical systems.

<img src="https://github.com/user-attachments/assets/f8ce13d7-89ce-4452-8ba4-38801e178507" width="66%">

### Piston A — Drivetrain / Flywheel

The first piston controls a pair of motors.

When extended, it pushes the gears into the drivetrain.

At the same time, it shifts the transmission into the **600 RPM high-speed ratio**.

When retracted, those motors are removed from the drivetrain and their power is redirected toward the flywheel.

The transmission simultaneously shifts into the **200 RPM high-torque ratio**.

This means that a single pneumatic action changes **both motor allocation and drivetrain gearing**.

<img src="https://github.com/user-attachments/assets/84457bd7-cdbb-4e13-b3da-d0b2fe4dae85" width="66%">

The piston activates both the clutch and the transmission at the same time.

### Piston B — Drivetrain / Intake

The second piston controls another pair of motors.

When extended, these motors provide power to the drivetrain.

When retracted, their power is redirected to the **first and second intake stages**.

The flywheel is controlled separately from these intake stages.

This allows the robot to distribute its motor power depending on whether it needs to prioritize:

- driving
- intake
- flywheel scoring
- defense

---

## 7. Transmission Mechanism

A sliding carriage moves one of the gears into position to change the drivetrain ratio.

<img src="https://github.com/user-attachments/assets/e69ff543-e6b7-4d5d-8dd1-4bb06be223cf" width="66%">

The carriage physically changes which gears are engaged.

This was one of the more mechanically difficult parts of the robot because the gears needed to engage reliably while the system was being actuated pneumatically.

The transmission also uses **beveled gears** to route power through the mechanism.

<img src="https://github.com/user-attachments/assets/4df69bf1-1443-488b-91c9-2255c24b680b" width="66%">

---

## 8. Chain Power Transfer

Some of the mechanical systems were separated by a significant distance.

Rather than adding another long gear train, I used a **sprocket and chain system** to transfer power between them.

<img src="https://github.com/user-attachments/assets/f362eb9f-fed3-469a-b981-ec1b48c03f9d" width="66%">

A chain allowed the power to travel across the robot while keeping the mechanism compact and reducing the number of gears required.

---

## 9. Intake and Wing Design

The intake and wing had several important design requirements.

The wing needed to:

- remain relatively compact
- move vertically
- fit underneath the Long Goal
- have a smaller range of motion
- be easy to position inside the goal

I chose a **parallel four-bar linkage** for the wing.

A parallel four-bar is a linkage made from four connected arms where the moving section maintains approximately the same orientation throughout its motion.

In this robot, that means the wing stays **vertical and perpendicular to the floor** as it moves.

This made it much easier to position the wing inside the Long Goal.

---

## 10. Four-Bar Mechanism

The early development of the four-bar mechanism can be seen below.

<img src="https://github.com/user-attachments/assets/951a2255-c919-407d-8664-7df89594b5e9" width="66%">

The final four-bar mechanism is controlled by **two pneumatic pistons**.

The pistons push an **over-center linkage**.

Once the linkage passes its center point, it mechanically locks into position. This means the mechanism does not need continuous pneumatic force to remain raised.

<img src="https://github.com/user-attachments/assets/90e80fd0-cf7d-49cc-8f6e-e787f0387127" width="66%">

This reduced the amount of pneumatic force required to hold the mechanism in position and made the system more mechanically stable.

---

## 11. Chassis Architecture

Unlike a typical VEX drivetrain, where the motors are usually mounted inside the chassis rails, this design required the motors to be mounted **above the chassis**.

The motors were placed next to each other to make the power distribution system physically possible.

<img src="https://github.com/user-attachments/assets/f261bbe0-8719-4142-97cf-cd39a332b317" width="66%">

This unconventional motor placement was necessary because the drivetrain, transmission, and pneumatic clutches all needed to occupy the same region of the robot.

The chassis was therefore designed around the mechanical power-sharing system rather than treating the drivetrain as an isolated component.

---

## 12. Intake Development

The intake was developed in multiple stages.

The first stage uses a small arm to manipulate game elements and guide them into the rest of the intake.

<img src="https://github.com/user-attachments/assets/3516ad72-3f51-4269-8f1f-f887541e04b5" width="66%">

The complete intake frame can be seen below.

<img src="https://github.com/user-attachments/assets/55170800-4c27-43e2-9e45-18f21c5f980f" width="66%">

<img src="https://github.com/user-attachments/assets/cd7d7d56-4bcf-4ad4-a26b-40be98e935f1" width="66%">

The intake was designed as multiple stages so that game elements could be moved from the floor, through the robot, and toward the scoring mechanism.

---

## 13. Intake Assembly

The first two intake stages were mounted onto the robot before the rest of the mechanisms were completed.

<img src="https://github.com/user-attachments/assets/264850cc-c773-412e-949b-691faf843fd5" width="66%">

<img src="https://github.com/user-attachments/assets/5096daa0-a9e7-4aad-9409-381ec9920b1f" width="66%">

<img src="https://github.com/user-attachments/assets/8de26fd9-d26b-41e4-9a94-668a9b9d36c5" width="66%">

These views show the intake in both the closed and raised positions.

---

## 14. Ball Storage System

The front of the robot contains a **large basket** used to store balls as a reserve.

Instead of immediately feeding every ball through the scoring mechanism, the robot can collect balls into the basket and store them until they are needed.

This provides several advantages:

- Balls can be collected quickly.
- The robot can build up a reserve of scoring objects.
- Balls can be scored later when the robot is in a better position.
- The robot does not need to stop collecting every time it wants to score.

The balls are fed **upward from the bottom** of the robot.

This was different from V1, where the balls entered from the top and were essentially tossed into the system.

---

## 15. Defensive Mode

One of the advantages of the power distribution system is that the robot can switch away from its scoring configuration and prioritize drivetrain power.

In defensive mode, the drivetrain can use the **200 RPM high-torque configuration**.

This sacrifices speed for pushing power.

With more drivetrain motors available and the lower-speed gear ratio engaged, the robot is much better suited for pushing and holding position against another robot.

### Defensive Driving Test

[![Robot driving in defensive mode](https://img.youtube.com/vi/C5uM0KIjCk0/maxresdefault.jpg)](https://youtube.com/shorts/C5uM0KIjCk0?feature=share)

---

## 16. Weight Reduction and Custom Parts

Because the robot contained a large amount of mechanical hardware, weight became an important design constraint.

One of the small but useful changes I made was replacing the standard VEX shaft collars with custom-made plastic shaft collars.

<img src="https://github.com/user-attachments/assets/20fefcde-33f0-46e6-af50-c1f2a22f3413" width="66%">

The custom collars were significantly lighter than the standard metal components.

To manufacture them consistently, I also designed a **3D-printed jig**.

<img src="https://github.com/user-attachments/assets/8c86951e-ea83-42f1-b918-ac675b2c2f75" width="33%">

The jig made it possible to produce multiple plastic shaft collars with consistent dimensions.

This was a small change, but it demonstrated an important part of my design philosophy: reducing weight wherever possible without sacrificing the function of the robot.

---

## 17. Complete Robot Assembly

The final robot combines several systems into one compact mechanical package:

- Eight total motors
- Two pneumatic power-distribution clutches
- Two-speed drivetrain transmission
- Multiple gear trains
- Chain-driven power transfer
- Multi-stage intake
- Vertical four-bar wing
- Flywheel scoring system
- Large front ball storage basket
- Custom lightweight components

The main challenge was not designing each mechanism individually.

It was getting **all of the mechanisms to work together without interfering with each other**.

The drivetrain had to share motors with the intake and flywheel.

The transmission had to change ratios while also responding to the pneumatic clutch system.

The wing had to remain compact enough to drive underneath the Long Goal.

The intake had to fit around the drivetrain and scoring mechanisms.

This required designing the robot as one interconnected mechanical system rather than as a collection of independent mechanisms.

---

# Previous Robot — V1 Development

Before designing V2, I developed another robot during the same season.

V1 was an important part of the design process because many of the ideas used in V2 came from problems I encountered while building and competing with it.

---

## 18. Early V1 Design Concepts

These are some of the early sketches from V1.

<img src="https://github.com/user-attachments/assets/54f4748f-9ace-4621-84a7-013075337325" width="66%">

<img src="https://github.com/user-attachments/assets/7c582b40-9d73-449b-b7de-50eedddcd214" width="66%">

The sketches show the early development of the chassis, intake, hood, and game-element mechanisms.

---

## 19. V1 Ball Routing System

One of the most complicated parts of V1 was its hood.

The hood used **three separate pneumatic pistons** to determine where a ball would go.

This created **four different possible ball paths**.

<img src="https://github.com/user-attachments/assets/e860afbd-da1b-4683-bd47-85d5f88176ef" width="66%">

<img src="https://github.com/user-attachments/assets/215d4b5e-5108-4932-8ff4-c75e0347bb4b" width="66%">

<img src="https://github.com/user-attachments/assets/33f03e8f-628c-44df-b108-cfb477bb0f14" width="66%">

This allowed the robot to control the destination of each ball mechanically.

However, the system was significantly more complicated than what I eventually wanted for V2.

The experience taught me that adding more mechanical options is not always the best solution. A mechanism should provide enough flexibility to solve the strategic problem without introducing unnecessary complexity.

---

## 20. V1 Expandable Ramp

V1 also used an expandable ramp for game elements.

The amount of distance a game element traveled depended on whether the hood was raised or lowered.

<img src="https://github.com/user-attachments/assets/728b82bf-0c6b-48d7-979e-d001482723f3" width="66%">

The ramp allowed the robot to adapt the path of the game element depending on the configuration of the hood.

---

## 21. V1 Robot

The back view of the completed V1 robot can be seen below.

<img src="https://github.com/user-attachments/assets/ac7e817c-5c12-4226-b961-18bd81ed634f" width="66%">

The V1 design provided the foundation for many of the ideas that eventually became part of V2.

---

## 22. V1 Intake With Hood

A demonstration of the V1 intake and hood mechanism:

[![V1 intake with hood](https://img.youtube.com/vi/9tBNqNpJNY4/maxresdefault.jpg)](https://youtube.com/shorts/9tBNqNpJNY4?feature)

---

# 23. Design Iteration and Engineering Lessons

The development of these robots taught me that successful robotics design is not simply about building the most complicated mechanism possible.

The most important part is identifying the actual problem and designing the mechanism around it.

V1 showed me the limitations of relying heavily on winging.

As the competitive meta changed, the wing became less effective because fewer balls were available in the control zone.

That led to the flywheel strategy used in V2, where the robot could disrupt the opponent's control from a distance.

The motor-sharing gearbox came from a similar thought process.

Rather than accepting that the robot needed separate motors for every task, I looked for a way to **change the allocation of power mechanically**.

This eventually led to the pneumatic clutch system, two-speed transmission, chain drives, and gear trains working together as one system.

The final robot is the result of several iterations of:

> **Identify the problem → design a mechanism → test it → find its limitations → redesign it.**

That process is what I find most valuable about robotics. The final robot is not just a collection of mechanisms; it is the result of continuously adapting the design to solve increasingly specific problems.
```
