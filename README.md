# RoboGrammar

![](media/optimized.jpg)

*A selection of best-performing designs generated with RoboGrammar for four different terrains.*

## Prerequisites

Commands were tested on Ubuntu 18.04.

[CMake](https://cmake.org/download/) >= 3.8
* Check with `cmake --version`

GLEW
* `sudo apt-get install libglew-dev`

Python 3.6 or later + headers
* Check the Python version with `python3 —-version`. If new enough, install Python headers: `sudo apt-get install python3-dev`
* Otherwise, install the latest version of both: `sudo apt-get install python3.9 python3.9-dev`

Note: Newer versions of Python may be available through the "deadsnakes" PPA:

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
```

## Building (Linux, Mac OS)

`git clone https://github.com/allanzhao/RoboGrammar.git`

`cd RoboGrammar`

`git submodule update --init`

`mkdir build; cd build`

`cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo ..`

`make -j8` (replace 8 with the number of CPU cores available)

## Installing Python Packages

Make sure you are in the `RoboGrammar` directory.

`pip3 install virtualenv`

`python3 -m venv venv`

`source venv/bin/activate`

`python3 examples/design_search/setup.py develop`

`python3 build/examples/python_bindings/setup.py develop`

## Running Examples

Make sure you are in the `RoboGrammar` directory, and that the virtualenv is active:

`source venv/bin/activate`

Run MPC for selected designs, and visualize (change `-j8` to use more CPU cores):

`python3 examples/design_search/viewer.py RidgedTerrainTask data/designs/grammar_apr30.dot -j8 0, 7, 1, 13, 1, 2, 16, 12, 13, 6, 4, 19, 4, 17, 5, 3, 2, 16, 4, 5, 18, 9, 8, 9, 9, 8 -o`

`python3 examples/design_search/viewer.py FlatTerrainTask data/designs/grammar_apr30.dot -j8 0, 12, 7, 1, 12, 3, 10, 1, 3, 1, 12, 12, 1, 3, 10, 2, 16, 8, 1, 3, 12, 4, 1, 3, 2, 12, 18, 9, 18, 8, 5, 5, 1, 12, 6, 3 -o`

`python3 examples/design_search/viewer.py GapTerrainTask data/designs/grammar_apr30.dot -j8 0, 1, 1, 7, 1, 6, 10, 3, 2, 4, 10, 10, 3, 16, 4, 16, 18, 2, 5, 16, 8, 4, 8, 8, 18, 4, 5, 15, 9, 8, 8 -o`

`python3 examples/design_search/viewer.py FrozenLakeTask data/designs/grammar_apr30.dot -j8 0, 1, 1, 1, 6, 7, 10, 11, 13, 2, 4, 3, 4, 16, 8, 14, 4, 8, 3, 15, 15, 5, 3, 9, 8 -o`

## FAQs

I get the error "The RandR headers were not found"
* Install the X server development files: `sudo apt-get install xorg-dev`
