---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Hello and welcome to my project based on the Filipino flag

## **Template VGA Design**
### **Project Set-Up**

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSum.png">

### **Template Code**
The template I was given, simulated the VGA interface which works by sending analog signals of RGB and timing signals to paint the screen with various colours. This works by using binary coding, precision / timing, HSync and VSync pulses. 
With VGATop as the head design source, the clock, VGASync and the ColourStripes are sub headings.

### **Simulation**
The simulation uses the testbench code in order to simulate the clock, reset and signals in waveforms before synthesis and hardware implementation.

<img width="1285" height="580" alt="Screenshot 2025-12-15 115838" src="https://github.com/user-attachments/assets/454076b1-006e-4909-bb2e-c42efc83e646" />

### **Synthesis**
Every reset from the clock activates the vga sync in order to produce the colour stripes as it relies on the column and row to be transmitted. Multiplexers of their own colour (red / green / blue) are also conected to the VGASync in order for everything to function simultaneously. This sequence of operation outputs the colours produced in the demonstration.

<img width="1439" height="512" alt="Screenshot 2025-12-15 115927" src="https://github.com/user-attachments/assets/8bf5ada7-8ed1-4140-b67c-ec9266a7cd91" />

### **Demonstration**
After attching the cables and running the hardware manager, I was able to produce a screen that consisted of different coulours in seprate columns. This template given wasn't complicated as it contained less code, less math and will be a good baseline to start my own project on top of it. 

<img width="776" height="526" alt="Screenshot 2025-12-14 215553" src="https://github.com/user-attachments/assets/25e79c39-7583-41fc-8ac1-8840ee4c0329" />

## **My VGA Design Edit**

<img width="1100" height="669" alt="Screenshot 2025-12-15 115908" src="https://github.com/user-attachments/assets/e5ad6186-3fae-463f-85a8-183646d0c3e5" />

My design idea involved the flag of the Philippines as it still contained what we learned, with complexity of the triangle, three stars and a sun / circle contained in the triangle. Originally, I thought the triangle will be easy and that the circle and stars would take up majority of time because of physics. But I soon realised the triangle was also a hinderence as it also followed slopes and required advanced maths.


<img width="751" height="562" alt="Screenshot 2025-12-14 215519" src="https://github.com/user-attachments/assets/ce978d17-bced-4861-a5a9-2491edcb6b7b" />

(First design in trying to get triangle to point right, towards middle of screen)

### **Code Adaptation**
The only code that differs from the original template, is the output and logic section that contains binary code. 

<img width="791" height="701" alt="Screenshot 2025-12-15 114639" src="https://github.com/user-attachments/assets/88081b58-7d0e-4dad-af0f-f69425de3eae" />

To start, the screen was split horizontally. Pixels with a row value less than 240 are colored blue, forming the upper half, while pixels below that are colored red, forming the lower half. The triangle is layed on top of this, by checking every pixel against line equations and only those that satisfy the conditions are coloured white. But to get the shape, where the triangle points left : 

The two conditions: col < (row * 2 / 3) and col < ((479 − row) * 2 / 3), represent the two straight lines that meet in the middle. These equations are derived from the formula x = m·y + c. As row increases from top to bottom, the first equation widens the triangle, while the second narrows it again, together forming the triangular shape.

<img width="919" height="565" alt="Screenshot 2025-12-14 215446" src="https://github.com/user-attachments/assets/e3444251-76ab-4e5a-bbab-293b11883e44" />

(Second design with succesfull triangle)

Lastly, The sun is generated using the circular equation: (x−xc​)^2 + (y−yc​)^2 < r^2, with pixels inside the radius coloured yellow to form the sun within the triangle. The squared distances are used in order to avoid square roots because they are expensive in hardware due to more clock cycles being used.

### **Simulation**
As you can see in my simulation, clock alternates between 1s and 0s, reset stays zero and hsync, vsync and vid_on continues as 1s. This gives the view of a continuos image or colour on screen and gives me the all clear to start implementation.

<img width="1459" height="673" alt="Screenshot 2025-12-09 145528" src="https://github.com/user-attachments/assets/ae96d2e1-ec19-4083-b3e5-874a6b3d7bc4" />

### **Synthesis**
All the changes are contained in the colour stripes files, VGASync remained untouched as it required no changing. Because of this, the only difference compared to the template file given, are the amount of clocks. 

<img width="651" height="518" alt="Screenshot 2025-12-09 150509" src="https://github.com/user-attachments/assets/046d6bc8-af07-4353-b8dc-f1d34176744f" />

### **Demonstration**
When I began this project, I thought the flag would be achievable and that the stars would be the only minor setback to my time. But I soon realised after trying to build the triangle, it was a lot more complicated than it looked and gives me more of an eppreciation for the engineers who build these advanced images.

If I were to do this again, after my experience with these shapes, I would make a scenic view of a mountain rather than something mundane like a flag.

<img width="771" height="524" alt="Screenshot 2025-12-14 215619" src="https://github.com/user-attachments/assets/8a869462-e2a8-4c4d-b6bd-bdca947115ab" />

(Final design with a sun, but no stars)
