import random

class Player:
    def __init__(self, name, position):
        self.name = name
        self.position = position
        self.skills = {
            "passing": random.randint(1, 10),
            "shooting": random.randint(1, 10),
            "dribbling": random.randint(1, 10),
            "defending": random.randint(1, 10),
        }
        self.stamina = 100
        self.salary = 1000
        self.reputation = 0

    def train(self):
        for skill in self.skills:
            self.skills[skill] += random.randint(1, 3)
        self.stamina -= 10

    def play_match(self):
        self.stamina -= random.randint(5, 20)
        return random.randint(0, 3)  # Result of the match: 0 - loss, 1 - draw, 2 - win

    def negotiate_contract(self):
        self.salary += random.randint(100, 500)
        self.reputation += random.randint(1, 10)

    def get_attributes(self):
        return f"{self.name} - {self.position}\nSkills: {self.skills}\nStamina: {self.stamina}\nSalary: ${self.salary}\nReputation: {self.reputation}\n"


def main():
    player_name = input("Enter player name: ")
    player_position = input("Enter player position: ")

    player = Player(player_name, player_position)

    while True:
        print("\nPlayer Menu:")
        print("1. Train")
        print("2. Play Match")
        print("3. Negotiate Contract")
        print("4. View Attributes")
        print("5. Quit")

        choice = input("Enter your choice: ")

        if choice == '1':
            player.train()
            print("Training complete!")
        elif choice == '2':
            result = player.play_match()
            if result == 0:
                print("You lost the match.")
            elif result == 1:
                print("The match ended in a draw.")
            else:
                print("You won the match!")
        elif choice == '3':
            player.negotiate_contract()
            print("Contract negotiation successful!")
        elif choice == '4':
            print(player.get_attributes())
        elif choice == '5':
            print("Exiting the game.")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
