# Ball Tracking Robot
My ball tracking robot uses a camera to detect a red ball and follows it by moving in real time. It processes the camera feed to find the ball’s position and decides whether to move forward, turn left, or turn right based on where the ball is. If the ball isn’t visible, the robot spins in place to search for it again.

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Satya K. | Northville High School | Electrical Engineering | Incoming Junior


  
# Final Milestone

For my final milestone, I combined all the motor and camera code so that the robot could smoothly track and follow a red ball on its own. This step was all about getting everything to flow together in real time. At first, I had a frustrating problem: the robot would move forward for a second, then randomly spin, then go forward again, and repeat. I realized this was happening because the ball’s position wasn’t being updated often enough, so the robot kept losing track of it and switching into "search mode." To fix this, I rewrote the code so that the camera constantly refreshed and checked for the ball’s position during every part of the movement.

The code begins by setting up the PiCamera to capture live images and initializing all the motor pins using GPIO. I created custom functions like `forward()`, `leftturn()`, `rightturn()`, and `stop()` to control how the robot moves. The most important part is the `find_ball()` function. It takes an image from the camera, converts it to HSV (which makes detecting red easier), filters for red using a mask, and then finds the biggest red shape on the screen. It calculates the center of that shape so the robot knows where the ball is. In the main loop, the robot checks the ball’s x-position: if it’s in the center of the screen, it moves forward; if it’s off to one side, it turns until the ball is centered. If the ball disappears, the robot spins to look for it. I made sure `find_ball()` is called constantly during each of these steps so the robot always knows what’s happening. Once I made that change, the robot finally moved smoothly and kept following the ball without stopping or glitching. This milestone was really exciting because it meant I had fully finished the brain of the robot and everything was finally working together.


<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>




# Second Milestone

For my second milestone, I finished writing all the code that controls my ball tracking robot. This was a really big deal for me because I had never coded before, and I had to learn everything from scratch. At first, I didn’t understand how to make the robot move or how the camera could detect a ball, but I kept researching, testing, and learning what each part of the code actually did. There are a few main parts in my code. First, I set up the camera using PiCamera2 so it can constantly take pictures of what’s in front of the robot. Then I used OpenCV to process those images. I converted the images to HSV color, which made it easier to detect red, and then I used masking to find only the red areas in the picture. After that, I found the contours of the red object and figured out the center and size of the ball. I also created different functions to move the motors in different directions, like forward, left, right, and stop. Finally, in the main loop, the robot uses the ball’s position to decide what to do—if the ball is centered, it drives forward; if the ball is on the left or right, it turns until the ball is centered again. If it can’t see the ball, it spins in place to search for it. Writing this code was definitely one of the hardest parts of the project, but also the most fun and rewarding, because now my robot can actually see and follow a red ball on its own—and I understand how it all works.


<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


# Milestone 1: Chassis Assembly and Wiring Completed
For the first milestone of my ball tracking robot project, I focused on building the chassis and wiring all the essential components.

Chassis Setup
I assembled a transparent acrylic chassis that holds two yellow DC gear motors for movement and a battery pack to power the system. The structure is lightweight and sturdy, designed to carry all electronics securely.

Electronics and Wiring
I connected the motors to an L298N motor driver, which allows for direction and speed control via GPIO pins on a Raspberry Pi 4. I also wired an HC-SR04 ultrasonic sensor to the Pi for obstacle detection, mounted on a breadboard along with jumper wires for easy prototyping.

Camera Integration
A Raspberry Pi Camera Module is attached via a ribbon cable and will later be used for ball tracking through computer vision.

With the chassis assembled and all electronics wired up, the robot is now ready for programming and sensor testing in the next phase

![Headstone Image](chassis and wiring.png)


# Schematics 
![Headstone Image](schematics.png)


# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

  # Starter Project

For my project, I’m building a mini retro game console using a hardware kit. It includes a pre-programmed PCB, buttons, resistors, a screen, and other components that I’ll solder onto the board. So far, I’ve reviewed the instructions and identified each part. A future challenge will be learning to solder accurately, but I plan to practice and follow each step carefully to complete the build and get the game running. Since my previous milestone, I’ve soldered several key components onto the PCB, including resistors, buttons, and the screen. This was my first time soldering, and I was surprised by how precise and steady-handed the process needs to be. At first, I struggled with getting clean connections, but after some practice, my technique improved. Before the final milestone, I need to finish soldering the remaining components and test the board to ensure the game runs properly. Since my previous milestone, I fully assembled the retro game console by successfully soldering all components to the PCB. One of my biggest challenges at BSE was learning to solder precisely, but completing the project without errors felt like a huge win. I gained hands-on experience with circuit boards, hardware assembly, and how code interacts with electronics. Moving forward, I hope to learn more about how to write and upload code to microcontrollers, and eventually design my own circuits from scratch
![Headstone Image](IMG_7048 (2) (1).png)
# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

To watch the BSE tutorial on how to create a portfolio, click here.
