# Synergy-Chess

Synergy-Chess is the public project of "py-goratschin" (https://github.com/feldi/py-goratschin#py-goratschin) which I have modified to allow 8 chess engines to run at the same time, instead of 2.

Synergy-Chess is a "chess engine" that supports the UCI chess protocol and combines 8 chess engines into one. In the goratschinChess.py file, the names of the 8 chess engines are : boss, counselor, counselor2, counselor3, counselor4, counselor5 and counselor6, counselor7

Synergy-Chess includes 8 clones of the same CE each with a different NNUE network; the rest of the configuration is the same for all clones, including the opening book, the ending table and the hash memory (to perform a test we recommend using 8 clones of Stockfish 15)

Synergy-Chess selects the "best move" to send to the GUI with the majority system of 7 chess engines. In case of a tie if a group of CE has the same move as the chess engine number 8, Synergy-Chess chooses that move, but if not, the system rewards the group with the highest positional score, finally, if all the engines express a different opinion, in this case we choose the move of the chess engine number 8.


# Decision-making system by majority and score #

# Note: chess engine = CE

Synegy-Chess chooses the Best Move to be sent to the GUI with 9 different criteria :

cr1) - Check absolute majority between 7 chess engines in the following chronological order ; 

majority 7 equal moves, 6 equal moves, 5 equal moves, 4 equal moves, and the first that is True is the Best Move

Absolute Majority between 7 chess engines is always the priority criterion ;

if between 7 CE there is no absolute majority of 7, 6, 5 or 4 equal moves, we move on to the next verification - cr 2)


cr2) - Check if between 7 CE there is a group of 3 CE with equal moves and compare with the verdict of the CE n ° 8 ;

if a group of 3 CE has the same move as CE n ° 8, this is the Best Move, but if not, proceed to the next check - cr3) 


cr3) - if between 7 CE 3 CE agree and 3 CE agree but with a different move from first group. in this case the Best Move is :

score move CE / 1 - score move CE / 2 

if diff > = 0 : best move = move CE / 1 

if diff < 0 : best move = move CE / 2


cr4) if between 7 CE there is an absolute majority of 3 CE with equal moves and if is True this is Bst Move, but if not, proceed to the next check - cr5)


cr5) - Check if between 7 CE there is a group of 2 CE with equal moves and compare with the verdict of the CE n ° 8 ;

if a group of 2 CE has the same move as CE n ° 8, this is the Best Move, but if not, proceed to the next check - cr6)


cr6) - if between 7 CE 3 groups of 2 CE agree but each group has a different move, the Best Move is :

score move CE / 1 - score move CE / 2

score move CE / 1 - score move CE / 3

score move CE / 2 - score move CE / 3

if score move CE / 1 - score move CE / 2 >= 0 and score move CE / 1 - score move CE / 3 >= 0 : best move = move CE / 1

if score move CE / 1 - score move CE / 2 >= 0 and score move CE / 1 - score move CE / 3 < 0 : best move = move CE / 3

if score move CE / 1 - score move CE / 2 < 0 and score move CE / 2 - score move CE / 3 >= 0 : best move = move CE / 2

if score move CE / 1 - score move CE / 2 < 0 and score move CE / 2 - score move CE / 3 < 0 : best move = move CE / 3



cr7) -  if between 7 CE 2 CE agree and 2 CE agree but with a different move :

score move CE / 1 - score move CE / 2

if diff >= 0 : best move = move CE / 1

if diff < 0 : best move = move CE / 2


cr8)  if between 7 CE there is an absolute majority of 2 CE with equal moves and if is True this is Bst Move, but if not, proceed to the next check - cr9)


cr9) -  the CE all give different moves : best move = move of chess engine number 8





# CONSIDERATIONS 
Synergy-Chess is suitable for games ranging from 40 minutes upwards and the system should bring a slight increase in the ELO score of the chosen chess engine, in short, the inspiration and variety of analysis induced by the 7 different NNUE networks should prevail, and if you have a latest generation CPU, the advantages of the system also increase.

It is true that the single opponent chess engine analyzes more in depth because the multiple chess engine is obliged to divide the processing power of the CPU among the 7 chess engines, however it seems that such depth of analysis is sufficiently qualitative and reliable because the choice of Best Move derives from the comparison of a considerable number of chess engines, moreover the depth of analysis is not always essential.

At the moment there is no chess GUI that allows you to create and configure a group of chess engines that work in synergy like Synergy-Chess, so it would be interesting if some chess GUI implemented such a system to simplify its use and make it accessible even to who do not has familiar with Python


# System Requirements

1 - Python 3 or later installed on your PC (https://www.python.org/downloads)

2 - approximately - two GB of hard disk space

3 - the Eman Chimera program to configure the .exe clones of the 7 chess engines

4 - GUI Arena 3.5.1 or Cute Chess

5 - Windows 10 operating system

6 - a little patience to fix everything .....


# Synergy-Chess installation instructions

.1 - Install GUI Arena 3.5.1 on your PC
http://www.playwitharena.de

.2 - Install Python 3.9 or 3.10 on your PC
https://www.python.org/downloads

.3 - create a single directory where all necessary files will be placed

.4 - in the created directory enter:

a) the .exe file of the desired chess engine from which you will then get the seven .exe clones with the correct configuration

b) the .bin file of the opening book

c) seven different NNUE networks that you can download from the site: https://tests.stockfishchess.org/nns

d) the .exe file of the Eman Chimera program which is used to configure the seven clones of the chess engine and create seven .exe files with the correct configuration

e) the goratschinLuncher.txt file, the goratschinLuncher.py file and the goratschinChess.py file

.5 - open the goratschinLuncher.txt file and replace the Xs with the path where the Python.exe file is located on your PC, then replace the other Xs with the path of the single directory created in which you have inserted the goratschinLuncher.py file : now, save the file with the same name but adding .bat at the end of the name, always in the same directory.

.6 - open the goratschinLuncher.py file and in engineFolderDefault replace the Xs with the path where the single directory you have created is located; the names in engineFileNames can be left unchanged but in the next point they will be mentioned with the same name. Now always save the file in the same directory and the same .py extension


.7 - Open the Eman Chimera program and in "Engine Name" write Combi01, 

then enable the 2 white squares, then click on ADD Uci Engine and in the new window click on Engine Path and in the new window enter the path of the single directory created in where you find the .exe file of the previously inserted chess engine and then select it, 

then click on configure and magically the window will appear in which you can configure the first clone of the chess engine; enter one of the seven NNUE networks that you have downloaded, you just need to type the complete name of extension .nnue, then choose from the various options available, Thread, Hash ... 

for the table of endings, SyzgyPath, you need to enter the path where the relative directory is located, if necessary you can download the 3-4-5 pieces version from this site: https://chess.massimilianogoi.com/download/tablebases/ ---- 

now click on Save and then again on Save, then click on add UCI Engine and in the new window click on Engine Path and in the new window enter the path of the single directory created in which the .exe file of the previously inserted chess engine is located and always select the same .exe file of the chess engine and repeat the configuration by entering identical parameters, including the first NNUE network that you have already entered in the previous step, then Save, now click Create Eman Chimera Engine and in the new window enter the path of the s created single directory in which Eman Chimera will insert the correctly configured Combi01.exe file and a Combi01.xml file

REPEAT the whole procedure for another 6 times, remembering however that in step 2 in Engine Name you will write Combi02 and in the double configuration of the chess engine you will insert a different NNUE network and so on up to step seven, Combi07


.8 - last step: open the GUI Arena and install the goratschinLauncher.bat file as a new chess engine and then on the Engine menu, Manage enable the UCI function and not Autodetecd. If you don't see the .bat file, just enable viewing of all files.

.9 - Have fun con Synergy-Chess
