# Yinsh-Bot
An AI bot that plays the game of yinsh.

## Game Flow
### Opening Game Strategy
For the opening game moves, a lookup strategy is to be followed. Find databases of previously played games and check the best moves for placing the rings.  
Some common strategies:  
1. Place the ring at the center
2. Block the opponent rings
3. One of the rings on the corners
4. Rings on separate lines
5. Rhombus Arragement

### Heuristic Search
Follow depth limited alpha beta pruning minimax search for upto 6-10(?) plyies.

### End Game Strategy
Detect the point when the end game strategy is to be followed (three rings remaining, probably).

## Heuristic
The heuristic function that shall be used for the current project:  
`h(n) = w1*f1(n) + w2*f2(n) + ... + wk*fk(n)`  
where,  
h(n)            -> Heuristic at state n  
f1, f2, ..., fn -> Feature values at state n  
w1, w2, ..., wn -> Weights of respective features  

## Features
Probable list of features:
1. ~~Number of markers in a row of 4~~ OR Number of rows of 4 markers [Both self and opponent] :heavy_check_mark:
2. ~~Number of markers in a row of 3~~ OR Number of rows of 3 markers [Both self and opponent] :heavy_check_mark:
3. Number of rows that are not flippable in the next move :heavy_check_mark:
4. Number of opponent rows that are not flippable in the next move [Both self and opponent] :heavy_check_mark:
5. A ring sharing a row of opponent markers 
6. Number of blocked self rings (and opponent rings) :heavy_check_mark:
7. Corner Occupancy

## Weights of Features
Play two bots with similar features, with the exception of one of the features. One of the bots shall learn and the other shall be learning.  
The teacher bot shall be the winner bot from the previous game and the student bot shall improve its features, with respect to the teacher bot. Once the student bot shall start performing better, switch positions.

## Further Considerations
1. Transitional changes for evaluating heuristics
2. Random moves with some small probability

# To-do  
- [x] Add ring for player  
- [x] Select ring and move to some position  
- [x] Select ring + move ring + remove k markers + remove specific ring  
- [x] Remove k markers + remove specific ring + select ring + move ring  
- [x] Remove k markers + remove specific ring + select ring + move ring + remove k markers + remove specific ring  
- [ ] Complete get successor function
- [x] More than k in row then we have a choice as to what to remove
- [ ] Now move ordering orders the moves when returning

### Improvements
- [] isFlippable calls updateRingPosition(). Can the calls be reduced?