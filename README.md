import random

def hangman():
    word_list = ["apple", "banana", "mango", "cherry", "orange"]
    chosen_word = random.choice(word_list).lower()
    display = ["_"] * len(chosen_word)
    lives = 7
    guessed_letters = set()

    print("Welcome to Hangman!")
    # Uncomment next line to cheat / debug
    # print("Pssst, the word is:", chosen_word)

    while lives > 0 and "_" in display:
        print("\nWord:  ", " ".join(display))
        print(f"Lives left: {lives}")
        guess = input("Guess a letter: ").lower().strip()
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue
        if guess in guessed_letters:
            print(f"You already guessed '{guess}'. Try another letter.")
            continue

        guessed_letters.add(guess)

        if guess in chosen_word:
            for idx, ch in enumerate(chosen_word):
                if ch == guess:
                    display[idx] = guess
            print("Correct!")
        else:
            lives -= 1
            print("Wrong!")

    if "_" not in display:
        print("\nCongratulations! You won 🎉 The word was:", chosen_word)
    else:
        print("\nGame over. You lost. The word was:", chosen_word)

if __name__ == "__main__":
    hangman()
