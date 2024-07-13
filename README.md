**Introduction**

For our final project we created a Mini golf like game using the FPGA hardware
resources. Our game was entirely playable on a USB keyboard connected to the fpga using the
MAX3421E USB host controller. Our game consisted of a start screen like any game, and we
aimed for a retro look to save memory and replicate NES games. The game had a top-level view
of golf course that we sourced online and uploaded as a ROM file into the on-chip BRAM of the
FPGA. The map had water, sand and trees replicating a real golf course. All the graphics we used
were uploaded on the BRAM as a Rom file using the ImagetoCOE tool. We gave the user
freedom to hit the ball in 12 directions and with 3 different power levels so that they could “Putt”
the ball in less than 14 shots in the hole. The user had to choose direction first with the help of
“A” and “D” keys on the keyboard. Once they are satisfied with direction, they had hit the
“Enter” on the keyboard to confirm their selection and move on to choose a power level. They
could choose between 3 power levels by using the “Up” and “Down” arrow keys on the
keyboard and again to confirm their selection they had to hit enter. Once this was done the ball
would be set in motion and based on any traps like sand or water the gameplay would change.
The game would end either if the ball entered the hole or if the number of shots taken exceeded
14.

------------------------------------------------------------------------------------------------------

**List of Features**

**Background & Display features:** The background was sourced online and using the Image to
COE tool we created a ROM file and uploaded into the BRAM. We accessed this map through
its RGB values pixel by pixel using DrawY and DrawX. The same process was done for the start
screen, end screen, power bar, score display and compass. To save the limited BRAM space we
had to shrink the start and end screen to 50% of screen size.

**Ball:** The ball was not a sprite but manually drawn using the same logic and formula from lab 6.
The ball position was used to determine if it was in Water, Sand, Grass or the hole and the
appropriate flag variables were toggled to control the FSM. The motion of the ball was
controlled in the FSM and ball file. The control unit, based on the direction and power counter
set the intial motion of the ball. In the ball file the subsequent motion of the ball was controlled
where variable friction was applied based on ball position to slow the ball down and stop it.

**Traps:** We had majorly two types of traps, water, and sand. These were detected based on the X
and Y positions of the ball which were logic variables declared by us. If the player entered the
water the ball would immediately go back to the restart position letting them continue the game
but back from the start as a penalty. If they entered the sand trap their motion would be curtailed
as the ball would move slowly and friction would be high.

**Score Display:** We used a register to track the number of shots taken by the player and displayed
it using sprites on the screen.
Collisions: To allow the player to continue playing even if the ball would leave the screen, we
added boundary collisions for the right and down boundaries of the screen. For the top wall we
kept it as a surprise, we turned the collisions off and let the ball wrap and move from the
opposite wall making it harder for them to play.

------------------------------------------------------------------------------------------------------

The final lab project was an interesting opportunity for us develop a basic version of a
game designed by us. We gained a deep understanding of how the MicroBlaze and FPGA work
together to enable dynamic projects. Over the two weeks we spent on this project, we learned a
great deal. We realized towards the end opportunities to optimize our game and in hindsight
realize a host of features we could add to make the game more dynamic and realistic. If the
BRAM's limitations were not a factor, we would have liked to incorporate multiple levels and
other elements to make the game more interesting. Overall, this project helped us solidify our
knowledge and understanding of building project on FPGA and using hardware like system
Verilog to execute complex gameplay logic.
