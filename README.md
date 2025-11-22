# HangManGame

import random

# ---- setup ----
words = ["apple", "brick", "cloud", "daisy", "eagle"]
secret = random.choice(words)
guessed = set()
wrong = 0
max_wrong = 6

# ---- helper to show the word ----
def display_word():
    return " ".join(ch if ch in guessed else "_" for ch in secret)

# ---- game loop ----
print("Hangman – guess the word!")
while wrong < max_wrong:
    print("\nWord:", display_word())
    print(f"Wrong guesses left: {max_wrong - wrong}")
    guess = input("Enter a letter: ").lower()

  if len(guess) != 1 or not guess.isalpha():
        print("Please type a single letter.")
        continue
    if guess in guessed:
        print("You already tried that.")
        continue

  guessed.add(guess)
    if guess in secret:
        print("Good guess!")
        if all(ch in guessed for ch in secret):
            print(f"\nYou win! The word was '{secret}'.")
            break
    else:
        wrong += 1
        print("Nope, not in the word.")
        if wrong == max_wrong:
            print(f"\nGame over – you ran out of guesses. The word was '{secret}'.")
