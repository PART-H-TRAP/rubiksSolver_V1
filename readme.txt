Less than 800 lines of code, completely solve the Rubik's Cube restoration problem

VC can compile and run, or use mingw's gcc to compile

Compile method under msys2 + mingw32 environment:

gcc -Wall -o cube cube.c

The total code is less than 800 lines, and the restoration speed is about 10s. Of course, it can be further optimized.


The meaning of some symbols:
F - front side, the white side after the program is run
B - back side, yellow side
L - left side, purple side (the standard Rubik's Cube should be orange, but the Windows console cannot display orange, so purple is used instead)
R - right side, red side
U - top side, blue side
D - bottom side, green side

Command description:

Rubik's Cube operation commands:
f - rotate the front side clockwise
f2 - rotate the front side 180 degrees
f' - rotate the front side counterclockwise

The same applies to other sides:
f2 f' b b2 b' u u2 u' d d2 d' l l2 l' r r2 r'

init - Reset the Rubik's Cube
rand - Randomly shuffle the Rubik's Cube, you can directly use rand or rand n, where n is the number of random shuffles
input - Enter the Rubik's Cube state, just follow the prompts
solve - Automatically restore the Rubik's Cube
help - Help information
exit - Exit the program

All commands are in lowercase letters.

Data structure and algorithm description:

In terms of data structure, each face is represented by a simple two-dimensional array. The key points are the implementation of the rotation operation of the six faces, the display of the Rubik's Cube state, and the state input.

In terms of algorithms, the heuristic breadth-first search is mainly used. The key points are the evaluation function of the Rubik's Cube state, pruning method, search algorithm, etc.

Of course, you have to understand the Rubik's Cube.

The program code is not large and is concise enough for careful appreciation. If you don't understand, you can ask questions.





When flag is equal to 0, it is mainly used to calculate the current cube state and whether it has reached the target state.
When flag is greater than 0, it is used to calculate how many points the current cube can get under the given target state, which is mainly used for pruning operations.
For example, I have already restored two layers. If the current expanded node is too far away from the two-layer restoration, I don’t need to keep this expanded node.

The search function is an algorithm implementation of breadth-first search, which uses open table + close table to expand nodes and search.
The open table is used as a queue, so it is breadth-first. Close is usually used to check whether a node has been expanded. In actual measurement, if this check is added, the speed becomes very slow, so the close table is not really used.



