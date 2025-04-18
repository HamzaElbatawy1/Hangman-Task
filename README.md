# Hangman-Task
import random

# Word list
words = ['python', 'computer', 'science', 'hangman', 'programming', 'developer']

# Select a random word
word = random.choice(words)
word_letters = set(word)
guessed_letters = set()
attempts = 6  # Number of allowed incorrect guesses

print("Welcome to Hangman!")
print("_ " * len(word))

while attempts > 0 and word_letters:
    guess = input("Guess a letter: ").lower()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single alphabetical character.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
    elif guess in word_letters:
        word_letters.remove(guess)
        guessed_letters.add(guess)
        print("Correct!")
    else:
        guessed_letters.add(guess)
        attempts -= 1
        print(f"Incorrect! You have {attempts} attempts left.")

    display = [letter if letter in guessed_letters else '_' for letter in word]
    print(" ".join(display))

if not word_letters:
    print(f"Congratulations! You guessed the word '{word}'")
else:
    print(f"Game over! The word was '{word}'")
