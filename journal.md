| Name    | Date Started | Project Name  | Description                                                           | Total Time |
|---------|--------------|---------------|-----------------------------------------------------------------------|------------|
| Filmona | July 25 2025 | GhostHub    | Custom split usb and hdmi port hub which connects to upstream devices through usbc receptacle   | 24.5 hours |

## Day 1 (3 hrs)  
Inspired by the hackclub jam ["Build a USB hub"](https://jams.hackclub.com/batch/usb-hub) I wanted to make one that instead used usbc upstream and would also include an hdmi port. The first part is pretty easy, but the hdmi port looks like a completely new path that I'll have to open up.  So after picking my usb hub chip that would be able to power 7 downstream usba connections, I lookd for an hdmi hub chip but that did not exist. I learend that I would have to use this display alt-mode chip which would I guess draw out the video and audio and output display port, but because I wanted hdmi I had to also find a display hdmi hub chip. After finding my parts I ended up with this simple setup.

![schematic with just components](images\components_schematic.png)

## Day 2 (5 hrs)  
I dove straight into the datasheets, because I knew that I would need those to make sure I wire my stuff correctly, and also for refrences because I had no idea what I was building. Also funnily enough finding the datasheets wasn't as easy as just going to jlcpcb because those only showed the demo version with only like 3 pages. But I was able to find datasheet for each one and the first thing I did was just try to make note of all the required and non required pins. 

Just reading wasn't enough so I also went through various Reddit/StackOverflow threads about the CC pins, about the DP alt-mode, about what to do with this confusion I had about if I needed two lanes or not. 

And through doing all this I slowly got to a semblance of a good looking schematic.

![Better looking schematic with some routing and pins filled in](images\WIP_schematic.png)

in the end I found little to no actual helpful substantial information.about how to combine a double two lane mux and the usb hub chip. 



## Day 3 (5 hrs)  
Today was mostly just trying to figure out if I was able to short the two data pins together for the usb hub and also find a way to seperate the two datapins for the TUSB1064 chip. 

Half way through my session of working on the schemeatic, tragedy struck me like it always does and I refreshed the page and hadn't saved the page which confused me becuase why isn't auto save not a default setting. So I spent 30 minutes setting it back up to the exact same position. 

However, sometime during a break while watching a pcb design competition, one of the contenstatns said that he just fed datasheets to chatgpt and whenever he got to any point where he needed to conslut the datasheet he would just ask chatgpt, which I starte ddoing. I wasn't too confident in what it was saying which is why I kept going back to check the datasheet but it did help out a lot in helping me confirm that I had to use a two lane datapin configuration for the tusb1064. So I had to come up with a new plan. 


## Day 4 (7.5 hrs)  
I decided to just make my new plan adding a seperate usbc receptacle for the hdmi that way there would be two. 

Sometime through working with the new schematic I decided to instead just use the usb downstream hub chip that was in the hackclub jam, which actually only introduced a new confusion for me which was about the crystals because in the jam, the crystal pins are connected to ground and another being NC. 

Anyways, I made the same saving error, blunder, mistake thing where I in the constant grind neither I or the server had saved my work so when I accidentatly let my laptop die, I lost all my progress. 

I did appreciate this though because it allowed me to make some small but important changes. 

Version 1:
![final schematicv1 ](images\final_schematicv1.png)

Version 2:
![final schematicv2](images\final_schematicv2.png)

That didn't take too long though, so I got straight into the pcb, which did take long. Really boring proccess. 

![final pcb design that passed drc check](images\final_pcb.png)


## Day 5 (4 hrs)  
Today was chill as all I have left is to make the case and find all the links for the BOM, I plan to use PCBA for this so I have to submit the BOM with the gerbers. 

After getting the BOM and the cpl(component placement list) I made a nice case.

![full angle of hub case assembly](images\full_angle_cad.png)

