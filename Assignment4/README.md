# Part 1
When we ran the model for 4 hours, we observed that the pathogen, the red cell on the left, began to interact with surrounding cells. The pathogen releases a chemical that diffuses into adjacent cells and weakens the cell walls. This phenomenon is visualized by a color change: the healthy, unaffected cells remain bright green, the cells near the pathogen turn brownish, and the pathogen remains red because it continues to release the chemical.

Below we can see how the model changes in 4 hours:

t=0:
![Alt text](time0.png)
First, we notice how the cells are a bright, uniform green, indicating healthy tissue. Initially, the red pathogen is present as a small, localized element on the left edge, and we see no changes in cells distant from the pathogen.

t=1
![Alt text](time1.JPG)
In this image, we see how, immediately after infection, the pathogen began spreading its chemical. The closest cells are already showing a color change toward brown, while the rest of the tissue remains green.

t=2:
![Alt text](time2.JPG)
After two hours, the pathogen began to enter the plant tissue, weakening even more surrounding cells.

t=3:
![Alt text](time3.JPG)
Now we can notice that the pathogen, in addition to penetrating even further into the plant tissue, has also grown larger, making more and more space between the cells.

t=4:
![Alt text](time4.JPG)
After four hours we observe how almost half of the tissue has turned brown and therefore weakened, the pathogen has taken hold among the cells and has become even larger, and even if some cells are still bright green, in a few hours they will also turn brown as the pathogen will continue to release chemicals.



# Part 2

The `CellHouseKeeping` function defines the behavior rules for each cell during the simulation. Specifically, it controls the growth of the pathogen cell and how the chemical travels through surrounding cells.

First, if the cell is type 2, i.e., the red pathogen, its target area is slightly enlarged (`EnlargeTargetArea(2)`), simulating the pathogen's growth.

Next, the code sets a baseline length for each cell's wall elements, if they don't already have one. This ensures that the structural properties of the cell walls are consistently initialized.

The most important part is the cell wall weakening mechanism. The function controls the level of the chemical released by the pathogen (`patho_chem_level`). If this level is high enough and the cell is not a pathogen, then:

- The cell can grow (`SetCellVeto(false)`),
- The cell wall stiffness is reduced (`setStiffness(stiffness_inf)`), with a reduction proportional to the amount of the pathogenic chemical present.

If the level of the chemical is too low, the cell wall stiffness is maintained at its normal value and the cell is prevented from growing (`SetCellVeto(true)`).

# Part 3

 Take a look at the cell to cell transport and cell dynamics and complete the sketch.
![Alt text](Exercise3.png)
From the cell-to-cell transport and cell dynamics we can see how the infection spreads. The pathogen produces chemical C(0), which weakens the stability of the plant cell wall. When the wall is weakened, diffusion rate it becomes faster, while stronger walls slow down diffusion. This means that the chemical spreads more quickly through weakened cells and more slowly through stable ones. As C(0) diffuses to neighbouring cells, their walls are also weakened, allowing the pathogen to gradually spread through the tissue.

# Part 4
Adjust the diffusion coefficient for the pathogen’s chemical (decrease by a factor of 10, then increase by a factor of 10). Document the simulations and describe in your own words what changes.

First, we look at the D parameter, which is the difussion rate, and see these values: 1e-05,4,0,0,0,0,0,0,0,0,0,0,0,0,0. Since in our code, we only use D[0], which is the diffusion rate for chemical 1, we will decrease it by 10.
![Alt text](Divide10_1.png)

Compared to the images from Part1, we can clearly notice that the difussion is much more slower now. In the first image we can see the tissue at time = 1:00:00.


![Alt text](Divide10_2.png)

Next image is captured at time = 2:00:00, where we can see that it's not that much of a difference between this and the first image.

![Alt text](Divide10_3.png)

Then, we can see at time = 3:00:00, that the pathogen (red) grows a bit bigger, but still, the difussion is slow, only a few of the cell were targeted.


![Alt text](Divide10_4.png)

Now, at time = 4:00:00, we notice that the chemical spread more, but still not comparble to the normal diffusion rate.


However, if we multiply the value of the diffusion rate by 10, we can observe a bigger difference.

![Alt text](Multiply10_1.png)

At t = 1:00:00, a much larger region around the pathogen showed reduced wall stability compared to the baseline, which means that the difussion was really fast.


![Alt text](Multiply10_2.png)

However, between t = 2:00:00, the progression of the infection front was less pronounced, and the spatial extent of weakened cells did not change substantially.


![Alt text](Multiply10_3.png)

Again, we can not observe any significant difference from 2h to 3h, even tho the pathogen seems to be bigger.


![Alt text](Multiply10_4.png)

In the end, at time = 4:00:00, we can notice a slightly change in color, a more darker one, which can indicate a more intens absortion of the chemical by the cells that were already infested.
