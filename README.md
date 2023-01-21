<h1><b>Circle images</b></h1>

Circle images with differential evolutionary algorithm from scratch.<br>

<div align="center">
    <img width="80%" src="https://github.com/ASASauqui/Circle-images/blob/main/readme_images/results/1.png?raw=true" />
    <p>Result after 200 circles.</p>
</div><br>

<h2><b>Used technologies</b></h2>

It is an optimization project made with:

<table align="center">
    <tr>
        <th align="center" style="text-align: center">
            Programming Language
        </th>
        <th align="center" style="text-align: center">
            Library
        </th>
    </tr>
    <tr>
        <td align="center">
            <img src="https://img.shields.io/badge/python-blue.svg?style=for-the-badge&logo=python&logoColor=white">
        </td>
        <td align="center">
            <img src="https://img.shields.io/badge/cv2-ab33c6.svg?style=for-the-badge">
        </td>
    </tr>
</table>
<br>

<h2><b>Installation and running (local)</b></h2>

### 1. Clone the repository
```
git clone <url>
```

### 2. Running and installations
Using Jupyter Notebook, you will be able to open and experiment with the .ipynb extension file, and you will be able to use code with the .py extension using regular Python.

Make sure you have CV2 installed in order to use the codes.
<br><br>

<h2><b>Codes division</b></h2>

You will find a total of 2 codes made in Python, of which 1 has the extension .ipynb, and the rest have the extension .py. The .ipynb file depends on the .py file to work, since the .py contains the implementation of the differential evolution algorithm made from scratch.

<ol>
    <li>
        <b>differential_evolution.py:</b>
        In this code is the implementation of the differential evolution algorithm made from scratch by us. It is very useful for the process of this project.<br>
    </li>
    <li>
        <b>circle_images.ipynb</b> This code is where the differential evolution algorithm will be run to create these images made of circles. Here will be the objective function, the parameters of the bounds, functions to display the image, etc. In general, everything necessary so that the result can be visualized.<br>
    </li>
</ol>
<br>

<h2><b>Folders division</b></h2>

Only 1 folder called "Datasets" is found.

<ol>
    <li>
        <b>Datasets:</b> This folder is where the images that we want to represent the version made with pure circles will go.<br>
    </li>
</ol>
<br>

<h2><b>Differential evolution</b></h2>

The differential evolution algorithm is a stochastic search algorithm, which works through a population of solutions called vectors, of the type:

<p align="center">
    𝑥 = < 𝑥<sub>1</sub> , 𝑥<sub>2</sub> , ... , 𝑥<sub>n</sub> >
</p><br>

This algorithm is useful to explore different search areas and gradually move the population to better regions in the search space, it is based on 3 important steps: mutation, crossover and selection of survivors.<br>
In the mutation, for each individual x<sub>i</sub>, another called v<sub>i</sub> is generated.<br>

<p align="center">
    𝑣<sub>i</sub> = 𝑥<sup>r1</sup> + 𝐹(𝑥<sup>r2</sup> − 𝑥<sup>r3</sup> )
</p><br>

Where F is a random number between 0 and 2.<br>
Later, in the crossover, what is sought is to combine the original vector x<sub>i</sub> with the previously created v<sub>i</sub> for the emergence of another vector called u<sub>i</sub>. This combination is made interleaved from the index 0 to k, and the decision to take for u<sub>ik</sub> the x<sub>ij</sub> or the v<sub>ij</sub>, is made by means of a probability 'Cr', which in this case is 0.5.<br><br>

<div align="center">
    <img width="30%" src="https://github.com/ASASauqui/Circle-images/blob/main/readme_images/math/1.svg?raw=true"/>
</div><br>

And finally, in the selection of survivors, the best individual between xi and ui is selected for a tournament, and the one who survives will be part of the next generation.<br><br>

<p align="center">
    𝑥<sub>i</sub> = 𝑏𝑒𝑠𝑡(𝑥<sub>i</sub> , 𝑢<sub>i</sub>)
</p><br>


<h2><b>Methodology</b></h2>

The general function of the algorithm is to add an amount 'n' of circles until completing the image and minimizing the objective function. In each iteration 'i', the differential evolution algorithm will decide which circle minimizes the objective function the most and comes closest to resembling the original image, in this way, each new circle it places will represent an improvement and, therefore, each time the created image will become more like the original. It will start from a black canvas the size of the original image, each time a new circle is added, it will become the new canvas, and so on iteratively until completing the stopping condition, which in this case is the amount ' n' of iterations.

<div align="center">
    <img width="70%" src="https://github.com/ASASauqui/Circle-images/blob/main/readme_images/methodology/2.png?raw=true" />
    <p>Control matrix and the image to calibrate.</p>
</div><br>

<ul>
    <li>
        <b>A. Load images</b><br>
        First, the image to be represented with circles was loaded and transformed to an RGBA format, so that it has the alpha component.<br><br>
        <div align="center">
            <img width="50%" src="https://github.com/ASASauqui/Circle-images/blob/main/readme_images/methodology/1.png?raw=true" />
            <p>Control matrix and the image to calibrate.</p>
        </div><br>
    </li>
    <li>
        <b>B. Bounds</b><br>
        7 types of bounds were specified, which are:<br>
        <ul>
            <li>'X' center position range (for circle 'x' position)</li>
            <li>'Y' center position range (for circle 'y' position)</li>
            <li>Radius range (circle radius)</li>
            <li>R range (red)</li>
            <li>G range (green)</li>
            <li>B range (blue)</li>
            <li>Alpha range (alpha)</li>
        </ul>
        In this case, the ranges that were given to each of these bounds were:<br>
        <ul>
            <li>'X' center position range (for circle 'x' position): [0, width]</li>
            <li>'Y' center position range (for circle 'y' position): [0, height]</li>
            <li>Radius range (circle radius): [5, width//2]</li>
            <li>R range (red): [0, 255]</li>
            <li>G range (green): [0, 255]</li>
            <li>B range (blue): [0, 255]</li>
            <li>Alpha range (alpha): [0.3, 1]</li>
        </ul><br><br>
    </li>
    <li>
        <b>C. Objective function</b><br>
        Given that 'P' is our array of parameters, 'X' is the image of the current canvas and 'Y' the target image (original image), we have that the objective function is:<br><br>
        <div align="center">
            <img src="https://latex.codecogs.com/svg.latex?f(P,X,Y)=\sum_{i=1}^{n}|Y_i-Z_i|"/>
        </div><br>
        Where 'Z' is the new canvas that will take the place of 'X'. This 'Z' canvas has the new circle made with the 'P' array parameters placed on the 'X' image. With this, we want to verify the difference between 'Y' and the image with the new circle and thus evaluate if there was an improvement or not.
    </li>
</ul><br>

<h2><b>Results</b></h2>

After only 200 circles an image close to the target image was achieved. The algorithm could have been given more time to get a more detailed picture, but this was enough to show that the algorithm works properly. It should be noted that the algorithm was optimized so that it could go faster, since in initial versions it was too slow.

<div align="center">
    <img width="80%" src="https://github.com/ASASauqui/Circle-images/blob/main/readme_images/results/1.png?raw=true" />
    <p>Result after 200 circles.</p>
</div><br>

