# Synergy-Chess

Synergy-Chess is the public project of "py-goratschin" (https://github.com/feldi/py-goratschin#py-goratschin) which I have modified to allow 7 chess engines to run at the same time, instead of 2.

Synergy-Chess is a "chess engine" that supports the UCI chess protocol and combines 7 chess engines into one. In the goratschinChess.py file, the names of the 7 chess engines are: chief, counselor, counselor2, counselor3, counselor4, counselor5 and counselor6

Synergy-Chess includes 7 clones of the same CE each with a different NNUE network; the rest of the configuration is the same for all clones, including the opening book, the table of endings and the hash memory (to perform a test we recommend the use of 7 clones of Stockfish 15)

Synergy-Chess selects the "best move" to send to the GUI with the majority system, instead when 2 or 3 groups of chess engines agree but with different moves between each group, in this case Synergy-Chess chooses the best move of the group with the highest positional score, finally, if all the engines express a different opinion, in this case the Boss chess engine move is chosen.


# Decision-making system by majority and score #

# Note: chess engine = CE

Synegy-Chess chooses the Best Move to be sent to the GUI with 5 different criteria :

cr1) - absolute majority of equal moves = Best Move (priority criterion)


cr2) - 3 CE agree and 3 CE agree but with a different move from first group. in this case the the Best Move is :

score move CE / 1 - score move CE / 2 

if diff > = 0 : best move = move CE / 1 

if diff < 0 : best move = move CE / 2

cr3) -  3 groups of 2 CE agree but each group has a different move, the Best Move is :

score move CE / 1 - score move CE / 2

score move CE / 1 - score move CE / 3

score move CE / 2 - score move CE / 3

if score move CE / 1 - score move CE / 2 >= 0 and score move CE / 1 - score move CE / 3 >= 0 : best move = move CE / 1

if score move CE / 1 - score move CE / 2 >= 0 and score move CE / 1 - score move CE / 3 < 0 : best move = move CE / 3

if score move CE / 1 - score move CE / 2 < 0 and score move CE / 2 - score move CE / 3 >= 0 : best move = move CE / 2

if score move CE / 1 - score move CE / 2 < 0 and score move CE / 2 - score move CE / 3 < 0 : best move = move CE / 3


cr4) -  2 CE agree and 2 CE agree but with a different move :

score move CE / 1 - score move CE / 2

if diff >= 0 : best move = move CE / 1

if diff < 0 : best move = move CE / 2


cr5) -  the CE all give different moves : best move = move of BOSS chess engine


# Note :
the system performs the best move based on the first TRUE condition it encounters and explores the conditions in the following chronological order :

01 - verification of an absolute majority of 7 equal moves

02 - verification of an absolute majority of 6 equal moves

03 - verification of absolute majority of 5 equal moves

04 - verification of an absolute majority of 4 equal moves

05 - check if there is 1 group of CE with 3 identical moves and another
group of CE with 3 identical moves but different from the first group

06 - absolute majority verification of 3 equal moves

07 - check if there are 3 groups of CE with 2 equal but different moves for each group

08 - check if there are 2 groups of CE with 2 identical but different moves for each group

09 - absolute majority verification of 2 equal moves

10 - if all the previous conditions are FALSE, and therefore there are 7 different moves, the system executes ELSE, ie the move of the CE Boss.


# System Requirements

1 - Python 3 or later installed on your PC (https://www.python.org/downloads)

2 - approximately - two GB of hard disk space

3 - the Eman Chimera program to configure the .exe clones of the 7 chess engines

4 - GUI Arena 3.5.1 or Cute Chess

5 - Windows 10 operating system

6 - a little patience to fix everything .....


# CONSIDERATIONS - 
Synergy-Chess is suitable for games ranging from 40 minutes upwards and the system should bring a slight increase in the ELO score of the chosen chess engine, in short, the inspiration and variety of analysis induced by the 7 different NNUE networks should prevail, and if you have a latest generation CPU, the advantages of the system also increase.

It is true that the single opponent chess engine analyzes more in depth as the multiple chess engine is obliged to divide the processing power of the CPU among the 7 chess engines, however it seems that such depth of analysis is sufficiently qualitative and reliable because the choice of Best Move derives from the comparison of a considerable number of chess engines, moreover the depth of analysis is not always essential.
