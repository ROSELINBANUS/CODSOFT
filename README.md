import random

def get_computer_choice():
    """Returns a random choice from rock, paper, scissors."""
    choices = ["rock", "paper", "scissors"]
    return random.choice(choices)

def get_user_choice():
    """Prompts the user to enter rock, paper, or scissors, and returns the choice."""
    while True:
        user_input = input("Enter rock, paper, or scissors: ").strip().lower()
        if user_input in ["rock", "paper", "scissors"]:
            return user_input
        else:
            print("Invalid choice. Please enter rock, paper, or scissors.")

def determine_winner(user_choice, computer_choice):
    """Determines the winner based on user and computer choices."""
    if user_choice == computer_choice:
        return "tie"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "paper" and computer_choice == "rock") or \
         (user_choice == "scissors" and computer_choice == "paper"):
        return "win"
    else:
        return "lose"

def play_game():
    """Main function to run the game loop."""
    wins, losses, ties = 0, 0, 0

    while True:
        print("\n--- New Round ---")
        user_choice = get_user_choice()
        computer_choice = get_computer_choice()
        print(f"Computer chose: {computer_choice}")

        result = determine_winner(user_choice, computer_choice)
        if result == "win":
            print("You win!")
            wins += 1
        elif result == "lose":
            print("You lose!")
            losses += 1
        else:
            print("It's a tie!")
            ties += 1

        print(f"\nScore: Wins {wins} | Losses {losses} | Ties {ties}")

        replay = input("\nDo you want to play again? (yes/no): ").strip().lower()
        if replay != "yes":
            break

    print("\nThanks for playing!")
    print(f"Final Score: Wins {wins} | Losses {losses} | Ties {ties}")

if __name__ == "__main__":
    play_game()
