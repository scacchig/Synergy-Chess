# Synergy-Chess

Synergy-Chess is an extension of the public project "py-goratschin" (https://github.com/feldi/py-goratschin#py-goratschin) which allows the simultaneous management of 8 chess engines, instead of 2.

Synergy-Chess supports the UCI chess protocol and the 8 chess engines are connected to their own default NNUE network and each has an ELO score greater than 3400 (March 31, 2022).

Synergy-Chess selects the "best move" to send to the GUI giving priority to the absolute majority system among 7 chess engines and in case of a tie if a group of chess engines has the same move as chess engine number 8, Synergy-Chess chooses that move, but in the negative case the system rewards the group with the highest positional score, finally, if all the chess engines express a different opinion, in this case the move of the chess engine number 8 is rewarded.


# Decision-making system by majority and score #

# Note: chess engine = CE

Synegy-Chess chooses the Best Move to be sent to the GUI with 9 different criteria :

cr1) - Check absolute majority between 7 chess engines in the following chronological order ; 

majority 7 equal moves, 6 equal moves, 5 equal moves, 4 equal moves, and the first that is True is the Best Move

Absolute Majority between 7 chess engines is always the "Priority Criterion" ;

if between 7 CE there is no absolute majority of 7, 6, 5 or 4 equal moves, we move on to the next verification - cr 2)


cr2) - Check if between 7 CE there is a group of 3 CE with equal moves and compare with the verdict of the CE n ° 8 ;

if a group of 3 CE has the same move as CE n ° 8, this is the Best Move, but if not, proceed to the next check - cr3) 


cr3) - if between 7 CE 3 CE agree and 3 CE agree but with a different move from first group. in this case the Best Move is :

score move CE / 1 - score move CE / 2 

if diff > = 0 : best move = move CE / 1 

if diff < 0 : best move = move CE / 2


cr4) if between 7 CE there is an absolute majority of 3 CE with equal moves and if is True this is Best Move, but if not, proceed to the next check - cr5)


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
With older generation CPUs we recommend a minimum time per game of 20/30 minutes, but with new generation CPUs the minimum optimal time is 10/15 minutes, so we could basically say that the minimum and optimal time for game of Synergy-Chess is directly proportional to the processing speed of the CPU used.

It is true that Synergy-Chess is obliged to divide the processing power of the CPU among the 8 chess engines, but if the minimum game time is respected as described above, the Sinergy-Chess analyzes will always be carried out within a "qualitative threshold sufficient ”because depth of analysis is not necessary in all positions ; therefore, by virtue of these hypotheses, the multiple analytical comparison of Synergy-Chess should avoid or at least significantly reduce any errors that may arise from the result of a single analysis.

At the moment there is no chess GUI that allows you to create and configure a group of chess engines that work in synergy like Synergy-Chess, so it would be interesting if some chess GUI implemented such a system to simplify its use and make it accessible even to who do not has familiar with Python


# System Requirements

1 - Python 3 or later installed on your PC (https://www.python.org/downloads)

2 - approximately - 850/900 MB of hard disk space

3 - GUI Arena 3.5.1 (http://www.playwitharena.de)

4 - Windows 10 operating system

5 - a little patience to fix everything.....


# Synergy-Chess installation instructions

.1 - Install GUI Arena 3.5.1 on your PC
http://www.playwitharena.de

.2 - Install Python 3.9 or 3.10 on your PC
https://www.python.org/downloads

.3 - create a single directory where all necessary files will be placed.


.4 - in the directory created insert all the files necessary for the correct functioning of Synergy-Chess ; for reasons of web space on github I uploaded all the necessary files to Google Drive at this address --- https://drive.google.com/file/d/1OgToe9d0b7HqlRTj_NpoPOW03Fkz3qeo/view?usp=sharing
List of files zipped in RAR files :

a) - 8 .exe files related to the 8 chess engines

b) - 4 files NNUE networks

c) - 1 goratschinLauncher.txt file, 1 goratschinLauncher.py file and 1 goratschinChess.py file

d) - if you have a CPU that supports the AVX2 or BMI2 architecture you can replace the 8 chess engines and if necessary the NNUE networks, also you have to rename the executables you add: SFa1, SFa2, SFa3, SFa4, SFa5, SFa6, SFa7 and SFa8, finally you have to open the goratschinLauncher.py file and in "options =" ​​you have to correct the options and you can also add other.


.5 - open the goratschinLuncher.txt file and replace the first path with the path where the Python.exe file is located on your PC, then replace the second path with the path of the single directory you created on your PC; now, save the file in the directory you created by typing gotatschinLauncher.bat in the File Name field; this .bat file will be installed as a chess engine in the GUI of Arena 3.5.1

.6 - open the goratschinLauncher.py file and in engineFolderDefault replace the existing path with the path where the single directory you created is located and save file ; the names in engineFileNames must be left unchanged.

.7 - last step: open the GUI Arena 3.5.1 and from the Engine Menu install the goratschinLauncher.bat file as a new chess engine (if you don't see the .bat file, enable the display of all files) and then from the Engine / Manage menu enable the UCI function and not Autodetecd, and we recommend enabling arena books ; finally, from the Engine Engine 1 menu (or right mouse button under the chessboard) click on configure and search "SyzygyPath" and enter the path where the endgames table is located on your PC; possibly you can download the Syzygy endings table here - https://chess.massimilianogoi.com/download/tablebases - we recommend the download of Syzygy 3-4-5 pieces table bases that take up only 1 GB of hard disk space ; the other values should not be changed, unless you know what you are doing...

.8 - Have fun with Synergy-Chess

.

# GUI Arena 3.5.1
<b>Tournament between Synergy-Chess and other chess engines</b>

a) - click on the "Engines / Tournament" menu, then in the window that appears click on "Settings" 

and set the various options, including "Elo rating" to 2850 or more


b) - then, still in the "Engines / Tournament" window, click on "Start / Quit" 

and enable "Restart engines after each game", and on "Additional delay during engine start phase" set "8 or 10 seconds";


"Additional delay" is very important because it gives Synergy-Chess the time it takes to restart 

the 8 chess engines at the end of each Round and receive New Game input only when the restart is complete.
