# Final-Project
Hero Villain Generator
import random

def generate_character():
    """Generate a hero or villain character."""
    character_type = input("Enter 'H' to generate a hero or 'V' to generate a villain: ").upper()
    while character_type not in ['H', 'V']:
        print("Invalid input. Please enter 'H' for hero or 'V' for villain.")
        character_type = input("Enter 'H' to generate a hero or 'V' to generate a villain: ").upper()

    first_name = input("Enter first name: ")
    last_name = input("Enter last name: ")
    
    species_list = ["Human", "Alien", "Mutant", "Robot", "Animal"]
    print("Choose a species from the following options:")
    for i, species in enumerate(species_list, 1):
        print(f"{i}. {species}")
    species_choice = input("Enter the number corresponding to your species choice: ")
    while not species_choice.isdigit() or int(species_choice) < 1 or int(species_choice) > len(species_list):
        print("Invalid input. Please enter a valid number.")
        species_choice = input("Enter the number corresponding to your species choice: ")
    species = species_list[int(species_choice) - 1]

    characteristics = ""
    weaknesses = ""
    if character_type == 'H':  # Generate characteristics and weaknesses for hero                         
        characteristics_list = ["Super strength", "Flight", "Telepathy", "Invisibility", "Healing"]
        weaknesses_list = ["Kryptonite", "Emotional trauma", "Fire", "Technology malfunction", "Water"]
        characteristics = random.choice(characteristics_list)
        weaknesses = random.choice(weaknesses_list)
    else:  # Generate characteristics and weaknesses for villain
        characteristics_list = ["Super intelligence", "Mind control", "Shapeshifting", "Teleportation", "Energy manipulation"]
        weaknesses_list = ["Morality", "Hubris", "Sunlight", "Love", "Holy objects"]
        characteristics = random.choice(characteristics_list)
        weaknesses = random.choice(weaknesses_list)

    character = f"Type: {'Hero' if character_type == 'H' else 'Villain'}\n" \
                f"First Name: {first_name}\n" \
                f"Last Name: {last_name}\n" \
                f"Species: {species}\n" \
                f"Characteristics: {characteristics}\n" \
                f"Weaknesses: {weaknesses}\n"

    return character

def generate_origin_story(character):
    """Allow the user to enter an origin story for the character."""
    origin_story = input("Enter origin story (limit to 250 words): ")
    while len(origin_story) > 250:
        print("Origin story exceeds 250 words. Please limit it to 250 words.")
        origin_story = input("Enter origin story (limit to 250 words): ")
    character += f"Origin Story: {origin_story}\n"
    return character

def save_character(character):
    """Save the character to a file."""
    with open("characters.txt", "a") as file:
        file.write(character + "\n")

def main(): 
    """Main function to generate hero/villain characters."""
    print("Welcome to Hero/Villain Generator!")
    while True:
        character = generate_character()
        print("\nCharacter Information:")
        print(character)
        keep_character = input("Do you want to keep this character? (Y/N): ").upper()
        while keep_character not in ['Y', 'N']:
            print("Invalid input. Please enter 'Y' to keep the character or 'N' to try again.")
            keep_character = input("Do you want to keep this character? (Y/N): ").upper()

        if keep_character == 'Y':
            character = generate_origin_story(character)
            save_character(character)
            print("Character saved to 'characters.txt'")
        else:
            print("Character not saved.")
        
        another_character = input("Do you want to generate another character? (Y/N): ").upper()
        while another_character not in ['Y', 'N']:
            print("Invalid input. Please enter 'Y' to generate another character or 'N' to quit.")
            another_character = input("Do you want to generate another character? (Y/N): ").upper()
        
        if another_character == 'N':
            print("Thank you for using Hero/Villain Generator!")
            break

if __name__ == "__main__":
    main()


     
Welcome to Hero/Villain Generator!
Enter 'H' to generate a hero or 'V' to generate a villain: h
Enter first name: Max
Enter last name: Lee
Choose a species from the following options:
1. Human
2. Alien
3. Mutant
4. Robot
5. Animal
Enter the number corresponding to your species choice: 3

Character Information:
Type: Hero
First Name: Max
Last Name: Lee
Species: Mutant
Characteristics: Super strength
Weaknesses: Kryptonite

Do you want to keep this character? (Y/N): y
Enter origin story (limit to 250 words): he likes dogs
Character saved to 'characters.txt'
Do you want to generate another character? (Y/N): n
Thank you for using Hero/Villain Generator!
