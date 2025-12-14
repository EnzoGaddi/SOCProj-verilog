---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Hello and welcome to my project based on the Filipino flag

## **Template VGA Design**
### **Project Set-Up**
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.

<img width="472" height="637" alt="Screenshot 2025-12-09 134830" src="https://github.com/user-attachments/assets/0bfe900d-3f0f-4360-9dba-96e5a65f02d7" />
### **Template Code**

The template I was given, simulated the VGA interface which works by sending analog signals of RGB and timing signals to paint the screen with various colours. This works by using binary coding, precision / timing, HSync and VSync pulses. 
With VGATop as the head design source, the clock, VGASync and the ColourStripes are sub headings.

### **Simulation**

### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.

### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
My design idea involved the flag of the Philippines as it still contained what we learned, with complexity of the triangle, three stars and a sun / circle contained in the triangle. Originally, I thought the triangle will be easy and that the circle and stars would take up majority of time because of physics. But I soon realised the triangle was also a hinderence as it also followed slopes and required advanced maths.

### **Code Adaptation**
The only code that differs from the original template, is the output and logic section that contains binary code. 

To start, the screen was split horizontally. Pixels with a row value less than 240 are colored blue, forming the upper half, while pixels below that are colored red, forming the lower half. The triangle is layed on top of this, by checking every pixel against line equations and only those that satisfy the conditions are coloured white. But to get the shape, where the triangle points left : 

The two conditions: col < (row * 2 / 3) and col < ((479 − row) * 2 / 3), represent the two straight lines that meet in the middle. These equations are derived from the formula x = m·y + c. As row increases from top to bottom, the first equation widens the triangle, while the second narrows it again, together forming the triangular shape.

Lastly, The sun is generated using the circular equation: (x−xc​)^2 + (y−yc​)^2 < r^2, with pixels inside the radius coloured yellow to form the sun within the triangle. The squared distances are used in order to avoid square roots because they are expensive in hardware due to more clock cycles being used.

### **Simulation**
The simulation uses the testbench code in order to simulate the clock, reset and signals in waveforms before synthesis and hardware implementation.

As you can see in my simulation, clock alternates between 1s and 0s, reset stays zero and hsync, vsync and vid_on continues as 1s. This gives the view of a continuos image or colour on screen and gives me the all clear to start implementation.
<img width="1459" height="673" alt="Screenshot 2025-12-09 145528" src="https://github.com/user-attachments/assets/ae96d2e1-ec19-4083-b3e5-874a6b3d7bc4" />

### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
<img width="651" height="518" alt="Screenshot 2025-12-09 150509" src="https://github.com/user-attachments/assets/046d6bc8-af07-4353-b8dc-f1d34176744f" />

### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
