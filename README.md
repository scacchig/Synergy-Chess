# Synergy-Chess

Synergy-Chess is the public project of "py-goratschin" (https://github.com/feldi/py-goratschin#py-goratschin) 
which I have modified to allow 5 chess engines to run simultaneously,  instead of 2. 

Synergy-Chess is a "chess engine" that supports the UCI chess protocol and combines 5 chess engines into one. 
In the goratschinChess.py file the names of the 5 chess engines are: 
boss, counselor, counselor2, counselor3, counselor4 

The 5 chess engines are activated simultaneously when they receive input from the GUI Arena or Cute Chess 
and finally the file goratschinChess.py sends a single "bestMove" at GUI Arena or Cute-Chess.

Synergy-Chess provides 52 different combinations of which : 
36 are managed with the decision-making system by majority 
15 with the decision-making system by score since 1 pair of engines agrees and another pair engines agrees but with a different move, 
finally, in last combination where all the chess engines emit different moves, the decision is of the chess engine called boss. 

# Majority Decision Making System
the majority decision-making system is composed of 52 different combinations with these criteria : 
- 1 - five engines agree, make the move of 5 
- 2 - four engines agree, make the move of 4 
- 3 - three engines agree and 2 are different from each other and different from 3, make the move of 3 
- 4 - three engines agree and two are different from 3 but agree with each other, make the move of 3 
- 5 - one pair of chess engines agrees and another pair agrees, but with a different move : 
this situation of equilibrium can occur 15 times and is managed with the decision-making system with scores  
- 6 - a pair of engines agrees and 3 engines are different from each other and from the torque, pair decide
- 7 - all engines give a different move, in which case it decides the chess engine called boss 

# Using Synergy-Chess

1 - Install Python on your PC (https://www.python.org/downloads), 
in this way the read of file goratschinChess.py and goratschinLauncher.py is safe, 
and the installing of the goratschinLauncer.bat file in the Arena GUI or Cute-Chess, too.

2 - after creating the following files, place them in the same directory : 
goratschinLauncer.bat 
goratschinChess.py 
goratschinLauncher.py 
and in the same directory also place the 5 files.exe of the chess engines you have chosen 

3 - install the goratschinLauncer.bat file as a new engine in the GUI of Arena or Cute Chess 

4 - if you want to customize the parameters of each single engine, you can use "Eman Chimera" 
(https://eman.zohosites.com/eman-chimera.html) which allows you to view the engine configuration, 
customize it and finally create the file.exe of the chess engine that will be placed together with the files.py and .bat 
Note : 
Eman Chimera requires the insertion of 2 engines, but it is possible to insert the same file.exe twice, 
then just set the first chess engine's move parameter to "0" and the second to 95, or 100, or 180...
this way only the first chess engine should work thus avoiding switching that could alter the functioning of Synergy-Chess



- CONSIDERATIONS - 
the best performance should be obtained by cloning the same chess engine 
and inserting a different NNUE file for each single chess engine, 
and also wanting a different opening book, in short, the fun and experimentation are yours....... 

Synergy-Chess is suitable for games ranging from 40/60 minutes and over, and performance improves with increasing set time.
