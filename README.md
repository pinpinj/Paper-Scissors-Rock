# PSR Game - Python
# Joshua Pinpin
# 26 May 2021
# This is a python code for a game of paper scissors rock 

import random

# this is for the computer generated answer
possible_outcome = ["Paper", "Scissors", "Rock"]

# so that the round number can be converted into words so that the user can read which round it is in words
round_words = {
    1 : "first",
    2 : "second",
    3 : "third",
    4 : "fourth",
    5 : "fifth"
}

# when the user enters a letter, it would come back with  the full word 
choices_converted = {
    "p" : "PAPER",
    "r" : "ROCK",
    "s" : "SCISSORS"
}

# start
print("Welcome User. This is a Paper, Scissors, Rock game.")
print("Ready to begin?")
starting = input("(Enter 'yes' or 'no') - ")

# preventing answers that are not yes or no
while starting != "yes" and starting != "no":
    starting = input("*Please enter a valid answer* - ")

# loops back to this until the user says no at the end
# start of code
while starting == "yes":
    
    # starting round 
    round_number = 1

    # starting lives for user and computer
    user_lives = 3
    computer_lives = 3

    # rules
    print("\n---\n")
    print("General Rules:")
    print("- The user (you) is playing against the computer.\n- Both you and the computer have 3 lives \n  (which will be shown before and after every round.)")
    print("- When you lose a round, you will lose a life.\n- The game ends when one person reaches 0 lives.")
    print("\nHow to win:")
    print("- Paper beats Rock.")
    print("- Rock beats Scissors.")
    print("- Scissors beats Paper.")
    print("\n- Enter 'P' for paper.")
    print("- Enter 'S' for scissors.")
    print("- Enter 'R' for rock.")

    # beginning game 
    begin_game = input("\nPress 'enter' to begin. - ")

    # loops until user presses enter
    while begin_game != "":
        begin_game = input("*Please press 'enter' to continue.* - ")

   # after every round, it will loop back so that it will continue the game 
   
    while begin_game == "":
        # will stop looping until the user or the computer lives reach 0      
        if user_lives == 0 or computer_lives == 0:
            if user_lives == 0:
                print("---\n")
                print("You have LOST")
            elif computer_lives == 0:
                print("---\n")
                print("You have WON!")
            break

        # will keep playing the game until reaches 0       
        elif user_lives != 0 or computer_lives != 0:
            print("\n---\n")
            print("* ROUND",round_number,"*")
            print("")
            print("Your Lives:", user_lives)
            print("Computer Lives:", computer_lives)
            print("")

            # the user's move/play
            user_choice = input("Enter your play. - ")

            # loop until user enters p, s or r
            while user_choice.lower() != "p" and user_choice.lower() != "s" and user_choice.lower() != "r":
                user_choice = input("*Please enter a valid answer* - ")

            print("-")
            
            # converts user's input to a full word instead of letter
            user_move = choices_converted[user_choice.lower()]
            print("Your move was:")
            print(user_move)
            
            # randomly generates an asnwer for the computer 
            computer_move = random.choice(possible_outcome)
            print("\nAnd the computer's move is:")            
            print(computer_move.upper())

            # if a tie 
            if user_move.lower() == computer_move.lower():
                print("\nIt's a tie!")
                print("Play the round again.")

            # if user enters p    
            elif user_move.lower() == "paper":
                if computer_move.lower() == "rock": 
                    # computer loses 1 life
                    computer_lives -= 1
                    print("\nPaper beats rock.\nYou WIN the", round_words[round_number], "round!")
                elif computer_move.lower() == "scissors":
                    # user loses one life
                    user_lives -= 1
                    print("\nScissors beats paper.\nYou LOSE the", round_words[round_number],"round!")
                # next round      
                round_number += 1

            # if user enters s    
            elif user_move.lower() == "scissors":
                if computer_move.lower() == "paper":
                    # computer loses 1 life
                    computer_lives -= 1
                    print("\nScissors beats paper.\nYou WIN the first round!")
                elif computer_move.lower() == "rock":
                    # user loses one life
                    user_lives = 1
                    print("\nRock beats scissors.\nYou LOSE the first round!")
                    # next round
                round_number += 1

            # if user enters r     
            elif user_move.lower() == "rock":
                if computer_move.lower() == "paper":
                    # user loses one life
                    user_lives -= 1
                    print("\nPaper beats rock.\nYou LOSE the first round!")                    
                elif computer_move.lower() == "scissors":
                    # computer loses one life
                    computer_lives -= 1
                    print("\nRock beats paper.\nYou WIN the first round!")
                # next round    
                round_number += 1

            # no matter which input, it will come to this line
            # loops it back to the begin_game input statment for the next round    
            begin_game = input("\nPress 'enter' to continue: ")

            # loops until user enters a valid answer (yes or no)
            while begin_game != "":
                begin_game = input("*Please press 'enter'* - ")

    # when user wins or loses, they will have a choice to play again             
    starting = input("\nWould you like to play again? - ")

    # loops until user enters valid answer 
    while starting.lower() != "yes" and starting.lower() != "no":
        starting = input("*Please enter a valid answer.* - ")

# prints this if user enters no for "starting" input
if starting.lower() == "no":
    print("---\n")
    print("Okay then bye... don't play. :(")
