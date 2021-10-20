# Preparation tasks

1. Read the [7-segment display tutorial](https://www.electronics-tutorials.ws/blog/7-segment-display-tutorial.html) and find out what is the difference between:

   - Common Cathode 7-segment display (CC SSD)
   - Common Anode 7-segment display (CA SSD)

_"The difference between the two displays, as their name suggests, is that the common cathode has all the cathodes of the 7-segments connected directly together and the common anode has all the anodes of the 7-segments connected together and is illuminated as follows._

_1. The Common Cathode (CC) – In the common cathode display, all the cathode connections of the LED segments are joined together to logic “0” or ground. The individual segments are illuminated by application of a “HIGH”, or logic “1” signal via a current limiting resistor to forward bias the individual Anode terminals (a-g)._

_The Common Anode (CA) – In the common anode display, all the anode connections of the LED segments are joined together to logic “1”. The individual segments are illuminated by applying a ground, logic “0” or “LOW” signal via a suitable current limiting resistor to the Cathode of the particular segment (a-g)."_

2. In the following table, write the binary values of the segments for display 0 to 9 on a common anode 7-segment display.

   | **Digit** | **A** | **B** | **C** | **D** | **E** | **F** | **G** | **DP** |
   | :-------: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :----: |
   |     0     |   0   |   0   |   0   |   0   |   0   |   0   |   1   |   1    |
   |     1     |   1   |   0   |   0   |   1   |   1   |   1   |   1   |   0    |
   |     2     |   0   |   0   |   1   |   0   |   0   |   1   |   0   |   0    |
   |     3     |   1   |   1   |   1   |   1   |   0   |   0   |   1   |   0    |
   |     4     |   1   |   0   |   0   |   1   |   1   |   0   |   0   |   0    |
   |     5     |   0   |   1   |   0   |   0   |   1   |   0   |   0   |   0    |
   |     6     |   0   |   1   |   0   |   0   |   0   |   0   |   0   |   0    |
   |     7     |   0   |   0   |   0   |   1   |   1   |   1   |   1   |   1    |
   |     8     |   0   |   0   |   0   |   0   |   0   |   0   |   0   |   0    |
   |     9     |   0   |   0   |   0   |   1   |   1   |   0   |   0   |   0    |

3. Use schematic of the [Multi-function shield](../../Docs/arduino_shield.pdf) and find out the connection of seven-segment display. What is the purpose of two shift registers 74HC595?

To convert a serial signal to a parallel one.
