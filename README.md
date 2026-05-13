<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>NAME : MOHAMMED SAFI F                      </h3>
<h3>REGISTER NUMBER : 212224060156              </h3>
<H3>AIM</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h3>Problem Description</h3>
<h4>Wumpus World</h4>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.  

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)
  
<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe.   

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.  
</p>

### PROGRAM
```python
wumpus = [
    ["Safe","Breeze","PIT","Breeze"],
    ["Smell","Safe","Breeze","Safe"],
    ["WUMPUS","GOLD","PIT","Breeze"],
    ["Smell","Safe","Breeze","PIT"]
]

# -------- INITIAL VARIABLES --------
row, column = 0, 0   # starting position
arrow = True         # player has arrow
player = True        # game loop
score = 0            # initial score

while player:
    choice = input("press u to move up\npress d to move down\npress l to move left\npress r to move right\n")

    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("move denied")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("move denied")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("move denied")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("move denied")

    else:
        print("invalid input")

    print("current location:", wumpus[row][column], "\n")

    # -------- ARROW LOGIC --------
    if wumpus[row][column] == "Smell" and arrow:
        arrow_choice = input("throw arrow? (y/n): ")

        if arrow_choice == "y":
            direction = input("u/d/l/r: ")

            if direction == "u" and row > 0:
                target = (row-1, column)
            elif direction == "d" and row < 3:
                target = (row+1, column)
            elif direction == "l" and column > 0:
                target = (row, column-1)
            elif direction == "r" and column < 3:
                target = (row, column+1)
            else:
                print("invalid direction")
                target = None

            if target and wumpus[target[0]][target[1]] == "WUMPUS":
                print(" Wumpus killed!")
                score += 1000
                wumpus[target[0]][target[1]] = "Safe"
            else:
                print("arrow wasted...")
                score -= 10

            arrow = False
            print("score:", score)

    # -------- GAME CONDITIONS --------
    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print(" Wumpus here! You died.")
        print("Score:", score)
        break

    if wumpus[row][column] == "GOLD":
        #  YOUR MISSING PART
        score += 1000
        print(" GOLD FOUND! You win!")
        print("Final Score:", score)
        break

    if wumpus[row][column] == "PIT":
        score -= 1000
        print(" Fell into PIT!")
        print("Score:", score)
        break
```
### OUTPUT

<img width="529" height="351" alt="image" src="https://github.com/user-attachments/assets/ee6c3a23-9bd1-4929-9d76-1c0b7335cbfa" />

### RESULT
Therefore, Wumpus World Problem using Python demonstrating Inferences from Propositional Logic solved successfully.
