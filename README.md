# 6-Motor Power Distribution Gearbox System

> One of the most ambitious and mechanically complex robots I have designed during my VEX Robotics career. This robot uses a combination of **pneumatic clutches, a two-speed transmission, gear trains, and chain drives** to dynamically redistribute motor power between three separate subsystems while simultaneously changing the drivetrain's gear ratio.

---

# Robot Design and Development

## 1. Design Evolution and Game Strategy

This robot was designed for the **VEX Robotics Competition game Push Back**.

In Push Back, robots collect balls and score them in goals. There are two **Long Goals** on the field. At the center of each Long Goal is a **Goal Control Zone**, which can hold up to three balls. Controlling this area provides additional points, making the position of the balls in the center of the goal strategically important.

After completing our first robot of the season, we determined that its overall architecture had significant potential. Our original plan was to recreate the same fundamental design while improving its CAD, manufacturability, reliability, and mechanical execution.

However, as we developed our strategy for Push Back, we identified a weakness in our original approach.

Our first robot relied heavily on **winging**, which involves using a mechanism to move balls out of the Long Goal and into another area of the field. This strategy was effective when there were many balls available to manipulate. However, as teams became better at clearing balls from the Goal Control Zone, fewer balls remained available for this strategy.

This became especially problematic when we were behind in score and our opponent controlled the balls in the Goal Control Zone. With our original robot, regaining control required several steps:

1. Collect enough balls to reach the center of the Long Goal.
2. Position the robot to interact with those balls.
3. Wing the balls out of the opponent's control.
4. Reposition the balls so that we could establish control ourselves.

We wanted a way to challenge the opponent's control much more quickly.

### Flywheel Strategy

Our solution was to add a **flywheel capable of launching a ball directly into the Goal Control Zone**.

The idea was to use the momentum of our launched ball to disrupt the three balls already occupying the control zone. If our ball enters one side of the group with enough momentum, that momentum can be transferred through the group of balls. Similar to the principle demonstrated by a Newton's cradle, the ball on the opposite side of the group can be forced out of the Goal Control Zone.

This meant that instead of physically collecting and repositioning multiple balls ourselves, we could potentially remove an opponent's ball from the control zone with a single launched ball.

Our strategy therefore changed from:

> **Collect → Position → Wing → Regain Control**

to:

> **Launch → Disrupt Opponent's Control → Establish Our Own Control**

This strategic change had a major impact on the mechanical design of the robot.

---

## 2. Early V2 Design Concepts

Our first step was to explore how the new strategy could be incorporated into the robot.

These early sketches helped us move away from simply rebuilding our previous robot and instead explore a new architecture centered around the flywheel, motor-sharing system, and revised intake.

![Early V2 robot sketch 1](https://github.com/user-attachments/assets/0ce3e39d-30e9-4f99-b411-dc54e31a6736)

![Early V2 robot sketch 2](https://github.com/user-attachments/assets/dad5ecb6-376f-41d8-9cac-937d451bd5dd)

![Early V2 robot sketch 3](https://github.com/user-attachments/assets/ff84876d-6cea-4f78-b8c7-db2a77808d86)

*Early sketches exploring the architecture of our V2 robot.*

---

# 3. Motor Allocation and Power Sharing

Adding a high-speed flywheel created a new engineering constraint: **power**.

Our previous intake system already had significant mechanical friction. Adding a flywheel capable of launching a ball into the Goal Control Zone required additional motor power.

We therefore needed to dedicate four motors to the intake and flywheel system.

This created a major problem.

If four motors were permanently dedicated to the intake and flywheel, only four motors would remain for the drivetrain. Four drivetrain motors did not provide enough pushing force for our robot. This was particularly dangerous in Push Back because robots frequently interact directly with each other while fighting for control of the field.

We therefore decided not to permanently assign every motor to a single subsystem.

Instead, we designed a **mechanical motor-sharing system**.

The motors themselves remain fixed to the robot. They do not physically move between subsystems. Instead, pneumatic pistons move gears that change the mechanical path through which the motors transmit their power.

This allows the same motors to be used by different subsystems depending on what the robot is doing.

### Motor Allocation

The robot can dynamically change between several configurations:

| Configuration | Drivetrain | Intake / Flywheel | Purpose |
|---|---:|---:|---|
| **High-Speed Drive** | 8 motors | 0 motors | Maximum drivetrain speed and power |
| **General Driving** | 6 motors | 2 motors | Fast movement while retaining intake capability |
| **Flywheel / Scoring** | 4 motors | 4 motors | Maximum intake and flywheel power |
| **High-Torque Drive** | 6 motors | 2 motors | Maximum pushing force with reduced drivetrain speed |

Rather than treating the eight motors as permanently assigned resources, we designed the robot so that motor power could be **redistributed mechanically during a match**.

---

# 4. Drivetrain Speed and the Torque Problem

We wanted our robot to be faster than most competing robots, so we initially designed the drivetrain around **2.75-inch wheels and a 600 RPM output speed**.

With eight motors powering the drivetrain, the 600 RPM configuration provided the speed we wanted while still providing sufficient torque.

However, when motors were transferred from the drivetrain to the intake and flywheel, the situation changed.

With only four motors powering the drivetrain, the 600 RPM configuration did not provide enough torque.

This created a serious problem. A robot with four motors on the drivetrain could move quickly, but it could also be pushed around too easily by an opposing robot.

This was especially dangerous while scoring. If an opponent could push us away from the goal while we were trying to score, the additional flywheel power would not matter because we would not be able to maintain our position.

We therefore needed to solve two problems simultaneously:

- **High speed** when enough motors were powering the drivetrain.
- **High torque** when motors were transferred to the intake and flywheel.

---

## 5. Two-Speed Transmission

Our solution was to integrate a **two-speed transmission** into the drivetrain.

The transmission changes the gear reduction between the motors and the wheels, allowing the drivetrain to operate at either:

- **600 RPM:** High-speed configuration
- **200 RPM:** High-torque configuration

The 200 RPM configuration is significantly slower, but the greater gear reduction increases the torque available at the wheels.

This allowed us to compensate for the reduced number of drivetrain motors when operating the flywheel.

Instead of accepting that four drivetrain motors would automatically make the robot easy to push, we used the transmission to trade speed for mechanical advantage:

> **4 motors + high gear reduction = significantly more pushing torque**

This allowed the robot to maintain useful pushing capability even while dedicating half of its motors to scoring.

![V2 chassis with two gear trains](https://github.com/user-attachments/assets/3ba639a0-098d-420d-9bfb-641e5098cbd4)

*The chassis contains two drivetrain gear paths. One provides the high-speed ratio used for fast movement, while the other provides a lower-speed, higher-torque ratio for situations where pushing power is more important.*

---

# 6. Mechanical Motor-Sharing System

The motor-sharing system uses two pneumatic pistons to redirect motor power through different gear paths.

The key design principle is that **the motors themselves remain stationary**.

Instead of moving the motors, we move the gears that determine where their power goes.

This allowed us to build a relatively compact system while still giving the robot multiple mechanical configurations.

## Piston A: Drivetrain and Flywheel Power Transfer

Piston A controls the power path between two drivetrain motors and the flywheel system.

When **Piston A extends**, it moves gears into mesh with the drivetrain gears. This connects the additional two motors to the drivetrain.

At the same time, the transmission shifts into the **600 RPM high-speed configuration**.

When **Piston A retracts**, those two motors are removed from the drivetrain power path and their power is redirected toward the intake/flywheel system.

The transmission simultaneously shifts into the **200 RPM high-torque configuration**.

Therefore, one pneumatic movement performs two mechanical functions:

1. It transfers two motors from the drivetrain to the flywheel system.
2. It changes the drivetrain from a high-speed ratio to a high-torque ratio.

### Early Four-Bar and Flywheel Development

Before finalizing the drivetrain and intake architecture, we developed the mechanisms that would support the flywheel.

![Early four-bar development](https://github.com/user-attachments/assets/951a2255-c919-407d-8664-7df89594b5e9)

*Early development of the four-bar mechanism that would eventually support the flywheel.*

![Four-bar over-center locking mechanism](https://github.com/user-attachments/assets/90e80fd0-cf7d-49cc-8f6e-e787f0387127)

*The four-bar was controlled by two pneumatic pistons acting through an over-center linkage. Once actuated, the linkage mechanically locked the mechanism in place, meaning the pistons did not need to continuously provide force to keep the mechanism raised.*

---

## Piston B: Intake and Drivetrain Power Transfer

Piston B controls another pair of motors and determines whether their power is sent to the drivetrain or the first and second stages of the intake.

When **Piston B extends**, these motors contribute to the drivetrain.

When **Piston B retracts**, these motors are redirected toward the first and second stages of the intake.

The flywheel is controlled separately from these intake stages.

This gives us another useful combination of motor allocation.

For example, when **Piston A is retracted and Piston B is extended**, the robot has:

- **6 drivetrain motors**
- **200 RPM drivetrain gearing**
- Reduced intake functionality
- High drivetrain torque

This became our preferred **defensive configuration**.

The robot sacrifices speed and some intake functionality in exchange for significantly greater pushing capability. This allows us to protect our own scoring area, resist opposing robots, and contest control of the field.

![Clutch system](https://github.com/user-attachments/assets/1ef59d96-4ca5-4c22-a56f-8f1f887b52ca)

*The clutch system used to redirect motor power between different subsystems.*

![Top view of the two clutches](https://github.com/user-attachments/assets/f8ce13d7-89ce-4452-8ba4-38801e178507)

*Top view showing the two clutches used to transfer motor power between the drivetrain, intake, and flywheel systems.*

---

# 7. Designing the Transmission

One of the most challenging parts of the system was creating a mechanism that could change the drivetrain's gear ratio at the same time that motor power was being redirected.

The transmission used a **sliding gear carriage** to move the appropriate gear into the drivetrain power path.

![Piston and transmission concept](https://github.com/user-attachments/assets/84457bd7-cdbb-4e13-b3da-d0b2fe4dae85)

*Early sketch showing how the pneumatic piston would simultaneously activate the clutch and transmission.*

![Sliding transmission carriage](https://github.com/user-attachments/assets/e69ff543-e6b7-4d5d-8dd1-4bb06be223cf)

*The sliding carriage moves a gear into the appropriate position, changing the drivetrain's gear ratio.*

![Beveled transmission gears](https://github.com/user-attachments/assets/4df69bf1-1443-488b-91c9-2255c24b680b)

*Beveled gears used as part of the transmission system in the chassis.*

### Transmitting Power Across the Robot

Because the motors and the mechanisms they powered were separated by significant distances, we could not always transfer power directly through a simple gear train.

Instead, we used **sprockets and chain** to transmit rotational power across the robot.

![Chain power transmission](https://github.com/user-attachments/assets/f362eb9f-fed3-469a-b981-ec1b48c03f9d)

*Sprocket and chain system used to transmit motor power between mechanisms separated by a significant distance.*

This allowed us to position the motors where they were most convenient for the chassis while still delivering power to mechanisms located farther away.

---

# 8. Chassis Architecture

The motor-sharing system required us to rethink the conventional VEX drivetrain layout.

In a typical VEX drivetrain, the motors are mounted within or alongside the chassis rails. Our design required significantly more motors to be positioned around the same area, while also leaving room for the gear trains that controlled the power distribution.

As a result, we moved the drivetrain motors **above the chassis rails** and arranged them next to each other.

![Raised drivetrain motors](https://github.com/user-attachments/assets/f261bbe0-8719-4142-97cf-cd39a332b317)

*Unlike a conventional VEX drivetrain, where motors are commonly mounted within the chassis rails, this design required the drivetrain motors to be raised above the chassis and positioned next to one another.*

This unconventional motor arrangement gave us the physical space needed to implement the additional gearing and power-transfer mechanisms.

---

# 9. Intake and Wing Design

The changes to our game strategy also influenced the design of the intake and wing.

We established several requirements:

1. The robot needed a **vertical wing**.
2. The wing needed to be compact enough to allow the robot to **drive underneath the Long Goal**.
3. The wing needed to maintain its orientation throughout its movement.
4. The intake needed to reliably collect and transfer balls.
5. The intake needed to integrate with the motor-sharing and flywheel systems.

## Parallel Four-Bar Wing

To satisfy these requirements, we designed the wing around a **parallel four-bar linkage**.

A parallel four-bar linkage maintains the orientation of the component mounted to it as the mechanism moves.

In our design, this means that the wing remains at the same angle relative to the floor throughout its entire range of motion.

![Intake four-bar development](https://github.com/user-attachments/assets/951a2255-c919-407d-8664-7df89594b5e9)

*Early development of the four-bar system.*

This was important because we wanted the wing to remain vertical while deploying and retracting.

A vertical wing also provided two advantages for our specific design:

- It required a smaller range of movement.
- Its geometry made it easier to position the wing into the Long Goal.

The four-bar therefore allowed us to combine a compact mechanism with predictable movement.

---

## 10. Intake Development

The first and second stages of the intake retained much of the architecture from our previous robot because that system had already proven effective at collecting and transferring balls.

The new design focused on integrating these stages with the flywheel, storage system, and motor-sharing mechanism.

![Intake arm](https://github.com/user-attachments/assets/3516ad72-3f51-4269-8f1f-f887541e04b5)

*Small intake arm used to manipulate game elements.*

![Full intake frame](https://github.com/user-attachments/assets/55170800-4c27-43e2-9e45-18f21c5f980f)

*Full intake frame during development.*

![Intake frame](https://github.com/user-attachments/assets/cd7d7d56-4bcf-4ad4-a26b-40be98e935f1)

*Additional view of the intake frame.*

![First two intake stages](https://github.com/user-attachments/assets/264850cc-c773-412e-949b-691faf843fd5)

![First two intake stages raised](https://github.com/user-attachments/assets/5096daa0-a9e7-4aad-9409-381ec9920b1f)

![Intake stages and four-bar](https://github.com/user-attachments/assets/8de26fd9-d26b-41e4-9a94-668a9b9d36c5)

*The first two intake stages mounted to the robot. The images show the four-bar in both its retracted and raised positions.*

---

# 11. Ball Storage System

The largest change to the intake was the **ball storage system**.

Our new robot uses a large basket at the front of the robot to store balls. We designed this area as a reserve so that we could collect balls earlier in the match and save them for later scoring opportunities.

This allowed us to treat stored balls as a resource that could be accessed when needed rather than requiring us to immediately score every ball we collected.

Unlike our previous robot, where balls entered the storage system from the top and were tossed into the storage area, the new robot feeds balls **upward from the bottom**.

This made the storage system more compatible with the new intake geometry and allowed us to create a larger, more controlled storage area.

---

# 12. Weight Reduction and Custom Parts

Because we wanted the robot to be as fast as possible, we looked for opportunities to reduce unnecessary weight.

One of the simplest areas for weight reduction was the large number of shaft collars used throughout the robot.

Instead of using standard VEX shaft collars everywhere, we designed and manufactured **custom 3D-printed plastic shaft collars**.

![VEX shaft collar comparison](https://github.com/user-attachments/assets/20fefcde-33f0-46e6-af50-c1f2a22f3413)

*Comparison between a standard VEX shaft collar on the left and our custom 3D-printed plastic version on the right.*

![Shaft collar manufacturing jig](https://github.com/user-attachments/assets/8c86951e-ea83-42f1-b918-ac675b2c2f75)

*3D-printed manufacturing jig used to consistently produce the custom plastic shaft collars.*

The custom collars reduced weight while still performing the same basic function as the standard components.

This was an example of a broader design philosophy we followed throughout the robot:

> **Remove weight wherever it does not contribute to performance, then use that saved weight where it matters.**

---

# 13. Complete Robot Assembly

After developing the individual systems, we integrated the drivetrain, transmission, clutches, intake, four-bar, flywheel, and storage system into a single robot.

![Robot with intake stages](https://github.com/user-attachments/assets/264850cc-c773-412e-949b-691faf843fd5)

*Robot during integration of the first two intake stages.*

![Robot with raised four-bar](https://github.com/user-attachments/assets/5096daa0-a9e7-4aad-9409-381ec9920b1f)

*Robot with the four-bar mechanism raised.*

![Full robot assembly](https://github.com/user-attachments/assets/8de26fd9-d26b-41e4-9a94-668a9b9d36c5)

*Full robot assembly during development.*

---

# 14. Testing

A major goal of the design was to ensure that the different mechanical configurations were useful in an actual match rather than simply working in isolation.

One of our primary tests was the robot's **defensive configuration**, where six motors power the drivetrain and the transmission shifts into the 200 RPM high-torque ratio.

[![Robot driving in defensive mode](https://img.youtube.com/vi/C5uM0KIjCk0/maxresdefault.jpg)](https://youtube.com/shorts/C5uM0KIjCk0?feature=share)

*Video of the robot driving in its defensive configuration.*

This configuration demonstrated the intended tradeoff between speed and pushing power. The robot is slower than its 600 RPM configuration, but the increased gear reduction allows the drivetrain to generate substantially more torque.

---

# 15. Previous Robot: V1 Development

The final robot was heavily influenced by what we learned from our first robot of the season.

Before developing the V2 architecture, we explored several complicated mechanisms on V1. These prototypes helped us identify which concepts were worth carrying forward and which needed to be redesigned.

### Early V1 Concepts

![Early V1 sketch](https://github.com/user-attachments/assets/54f4748f-9ace-4621-84a7-013075337325)

![Early V1 sketch](https://github.com/user-attachments/assets/7c582b40-9d73-449b-b7de-50eedddcd214)

*Early sketches from the V1 robot.*

![V1 back view](https://github.com/user-attachments/assets/ac7e817c-5c12-4226-b961-18bd81ed634f)

*Back view of the V1 robot.*

---

## 16. V1 Ball Routing System

One of the more complicated mechanisms on V1 was the ball-routing system.

We designed a mechanical "hood" that used **three separate pneumatic actuators** to determine the path a ball would take through the robot.

By changing the positions of these mechanisms, the robot could create **four different ball paths**.

![V1 hood mechanism](https://github.com/user-attachments/assets/e860afbd-da1b-4683-bd47-85d5f88176ef)

![V1 hood mechanism](https://github.com/user-attachments/assets/215d4b5e-5108-4932-8ff4-c75e0347bb4b)

![V1 hood mechanism](https://github.com/user-attachments/assets/33f03e8f-628c-44df-b108-cfb477bb0f14)

*The V1 hood used three separate pneumatic actuators to control which of four possible paths a ball would take through the robot.*

We also developed an expandable ramp because the distance a ball needed to travel changed depending on the position of the hood.

![V1 expandable ramp](https://github.com/user-attachments/assets/728b82bf-0c6b-48d7-979e-d001482723f3)

*Expandable ramp designed to accommodate the different distances a ball needed to travel depending on the hood position.*

[![V1 intake and hood](https://img.youtube.com/vi/9tBNqNpJNY4/maxresdefault.jpg)](https://youtube.com/shorts/9tBNqNpJNY4?feature=share)

*Video of the V1 intake and hood system.*

---

# 17. Design Iteration and Engineering Lessons

The V2 robot was not simply a more refined version of V1. The biggest improvement was in how we approached the design process.

Our strategy changed first.

That strategic change created a need for a flywheel.

The flywheel created a need for additional motor power.

The additional motor power created a drivetrain torque problem.

The torque problem led to the development of a two-speed transmission.

The limited motor count led to the development of mechanical power-sharing clutches.

The new mechanisms created packaging challenges that forced us to rethink the chassis, motor placement, intake, and power transmission.

The resulting design can therefore be represented as a chain of engineering decisions:

Changing Push Back strategy
            ↓
Need to directly disrupt the Goal Control Zone
            ↓
High-powered flywheel
            ↓
Increased motor requirements
            ↓
Dynamic motor power sharing
            ↓
Fewer motors available to drivetrain
            ↓
Insufficient drivetrain torque
            ↓
Two-speed transmission
            ↓
600 RPM high-speed ratio
            +
200 RPM high-torque ratio
            ↓
Adaptive drivetrain performance
