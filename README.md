UR sends poses to Python progam and asks stored poses from Python program.

The UR is used for leaktesting. The leak detector is connected to an input on the UR controller. A separate thread in the UR program 'watches' this input and when triggered sends the corresponding robot pose to the Python program. To be able to return 'collision-free' to these leak positions a third thread in the UR program is sending poses the python program at fixed time intervals. Both threads use a 'flag' to indicate whether the position that was sent is a leak position or a non-leak position. The Python program stores the received poses in a the order they arrive and can send the poses back to the UR program also indicating whether it was a leak position or non-leak position. This allows the UR robot to go along the same path and halt at leak positions for the operator to confirm he has seen (and possibly marked) the leak position.