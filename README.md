# word-game
import random
word_list = ["apple", "banana", "cherry", "date", "elderberry", "fig", "grape"]
random_word = random.choice(word_list)
tries = 0
username = input("Hello, What's your Name? ")
print("Hello", username + ",")

question = input("Would you like to play a word guessing game? [Y/N] ")
if question.lower() == 'n':
    print("Oh..okay")
elif question.lower() == 'y':
    print("I'm thinking of a word with", len(random_word), "letters.")
    
    guessed_letters = set()
    while True:
        print("Guessed letters:", ' '.join(sorted(guessed_letters)))
        guess = input("Have a guess (a letter or the whole word): ").lower()
        
        if guess == random_word:
            tries += 1
            print("You're right! You win! The word was", random_word, "and it took you", tries, "tries!")
            break
        elif len(guess) == 1 and guess.isalpha():
            tries += 1
            guessed_letters.add(guess)
            if guess in random_word:
                print(f"Good guess! The letter '{guess}' is in the word.")
            else:
                print(f"Sorry, the letter '{guess}' is not in the word.")
        else:
            print("Please guess a single letter or the entire word.")
        current_progress = ''.join([letter if letter in guessed_letters else '_' for letter in random_word])
        print("Current progress:", current_progress)
        if all(letter in guessed_letters for letter in random_word):
            print("Congratulations! You've guessed the word:", random_word)
            print("It took you", tries, "tries!")
            break
