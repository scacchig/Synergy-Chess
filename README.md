# Synergy-Chess

Synergy-Chess is the public project of "py-goratschin" (https://github.com/feldi/py-goratschin#py-goratschin)
which I have modified to allow the insertion of 5 chess engines instead of 2, moreover, 
my modified circumvents the decision scoring system by replacing it with the majority decision system

Synergy-Chess is a "chess engine" that supports the UCI chess protocol
and combines 5 chess engines into one.

In the goratschinChess.py file the names of the 5 chess engines are:
boss, counselor, counselor2, counselor3, counselor4

The 5 chess engines are activated simultaneously 
when they receive the input from the Arena or Cute Chess GUI, 
and the goratschinChess.py file sends a single "bestMove" 
to the GUI through a majority decision making system.

# Majority Decision Making System
the majority decision-making system is composed of 52 different combinations with these criteria : 
1 - five engines agree, make the move of 5 
2 - four engines agree, make the move of 4 
3 - three engines agree and 2 are different from each other and different from 3, make the move of 3 
4 - three engines agree and two are different from 3 but agree with each other, make the move of 3 
5 - two pairs of motors agree but the pairs are different from each other : 
in this case one of the couples decides alternating the choice in the possible 15 combinations 
6 - a pair of engines agrees and 3 engines are different from each other and from the torque, pair decide
7 - all engines give a different move, in which case it decides the move of the boss engine

# Using Synergy-Chess

1 - after creating the following files, place them in the same directory : 
goratschinLauncer.bat 
goratschinChess.py 
goratschinLauncher.py 
and in the same directory also place the 5 files.exe of the chess engines you have chosen 

2 - install the goratschinLauncer.bat file as a new engine in the GUI of Arena or Cute Chess 

3 - if you want to customize the parameters of each single engine, you can use "Eman Chimera" 
(https://eman.zohosites.com/eman-chimera.html) which allows you to view the engine configuration, 
customize it and finally create the file.exe of the chess engine that will be placed together with the files.py and .bat 
Note : 
Eman Chimera requires the insertion of 2 engines, but it is possible to insert the same file.exe twice, 
then just set the first chess engine's move parameter to "0" and the second to 95 or 100, 
this way only the first chess engine should work thus avoiding switching that could alter the functioning of Synergy-Chess



- CONSIDERATIONS - 
the best performance should be obtained by cloning the same chess engine 
and inserting a different NNUE file for each single chess engine, 
and also wanting a different opening book, in short, the fun and experimentation are yours....... 

Synergy-Chess is suitable for games ranging from 40/60 minutes and over, and performance improves with increasing set time.
