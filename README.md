# 🎮 PYTHON HANGMAN TUTORIAL 🎮
## A Step-by-Step Guide for Young Coders

---

## 👋 INTRODUCTION: LET'S BUILD A GAME!

Hey future coders! Today we're going to build a classic game called **Hangman** using Python. This game is super fun to play AND to code! By the end of this tutorial, you'll have your very own Hangman game that you can show off to your friends and family.

### What is Hangman? 🤔

Hangman is like a word-guessing game where:
- The computer picks a secret word
- You try to guess the word one letter at a time
- Each wrong guess brings you closer to "game over"
- If you guess all the letters before running out of tries, you win!

Think of it like those text messages where someone is typing "..." and you're trying to guess what they'll say next!

### What You'll Learn 🧠

- How to use **variables** to store game information
- How to use **lists** to keep track of letters
- How to use **loops** to keep the game running
- How to use **conditional statements** (if/else) to check guesses
- How to use **functions** to organize our code
- How to handle **user input** and give feedback

Let's get started! 🚀

---

## 🛠️ PART 1: SETTING UP OUR GAME

### Step 1: Create Your Python File

First, let's create a new file called `hangman.py`. This is where all our code will live.

### Step 2: Import the Tools We Need

```python
import random
```

**🤔 Why do we need this?**
- The `import random` line gives us special powers to make the computer pick random things
- It's like having a digital dice we can roll to pick a random word
- Without this, our game would be boring because we'd have to pick the words ourselves!

### Step 3: Create Our Word Bank

```python
# Word bank - the computer will randomly choose one of these words
word_list = ["python", "banana", "hangman", "gamer", "pizza", "laptop"]
```

**🤔 What's happening here?**
- We're creating a **list** called `word_list`
- A list in Python is like a container that holds multiple items
- Each word is inside quote marks (`"word"`) because they are **strings** (text data)
- The square brackets `[ ]` tell Python this is a list
- The `#` symbol starts a **comment** - text that Python ignores but helps us humans understand the code

### Step 4: Pick a Random Word

```python
# Computer randomly selects a word from our list
secret_word = random.choice(word_list)
```

**🤔 What's happening here?**
- `random.choice()` is a **function** from the random module we imported
- It's like reaching into a hat and pulling out one random item
- We store that random word in a **variable** called `secret_word`
- Variables are like labeled containers that hold information we want to use later

### Step 5: Create Placeholders for the Secret Word

```python
# Create blank spaces for each letter in the secret word
guessed_word = ["_"] * len(secret_word)
```

**🤔 What's happening here?**
- `len(secret_word)` counts how many letters are in our secret word
- `["_"]` creates a list containing just one underscore
- The `*` operator repeats that underscore as many times as there are letters
- So if the secret word is "pizza" (5 letters), `guessed_word` becomes `["_", "_", "_", "_", "_"]`
- This creates our hidden word display with blanks for each letter

### Step 6: Set the Number of Lives

```python
# Number of wrong guesses allowed
lives = 6
```

**🤔 What's happening here?**
- We're creating a variable called `lives` and setting it to 6
- This means the player gets 6 wrong guesses before losing
- We'll subtract 1 from this number each time they guess wrong

### Step 7: Welcome the Player

```python
# Welcome message
print("Welcome to Hangman! Can you guess the secret word? 🤔")
print("Your word:", " ".join(guessed_word))
```

**🤔 What's happening here?**
- `print()` is a function that displays text to the player
- `" ".join(guessed_word)` takes our list of underscores and joins them with spaces in between
- So `["_", "_", "_", "_", "_"]` becomes `"_ _ _ _ _"` which looks nicer for the player to see

---

## 🎮 PART 2: CREATING THE GAME LOOP

### Step 8: Start the Main Game Loop

```python
# Main game loop - keeps running until player wins or loses
while lives > 0 and "_" in guessed_word:
    # Game code will go here...
    pass
```

**🤔 What's happening here?**
- `while` creates a **loop** that keeps repeating as long as certain conditions are true
- `lives > 0` checks if the player still has lives left
- `"_" in guessed_word` checks if there are still letters to guess (underscores remaining)
- The loop will keep running until either the player runs out of lives OR all letters are guessed
- `pass` is just a placeholder - we'll replace it with our actual game code

### Step 9: Get the Player's Guess

```python
# Get player's guess
guess = input("\nGuess a letter: ").lower()
```

**🤔 What's happening here?**
- `input()` is a function that pauses the game and waits for the player to type something
- The text inside the parentheses is the prompt shown to the player
- `.lower()` converts the player's input to lowercase (so 'A' becomes 'a')
- This makes our game easier because we don't have to worry about uppercase vs lowercase

### Step 10: Check If the Guess is Correct

```python
# Check if the guessed letter is in the secret word
if guess in secret_word:
    print("🎯 Good guess! That letter is in the word!")
    
    # Fill in all matching letters
    for index, letter in enumerate(secret_word):
        if letter == guess:
            guessed_word[index] = guess
else:
    print("❌ Oops! That letter is not in the word!")
    lives -= 1  # Lose a life
```

**🤔 What's happening here?**
- `if guess in secret_word:` checks if the letter the player guessed is anywhere in the secret word
- If it is, we need to reveal all instances of that letter in the displayed word
- `for index, letter in enumerate(secret_word):` is a special loop that gives us both the position (index) and the value (letter) of each character in the secret word
- `if letter == guess:` checks if the current letter matches the player's guess
- `guessed_word[index] = guess` replaces the underscore with the correctly guessed letter at the right position
- If the guess is wrong, we reduce `lives` by 1 using the `-=` operator (shorthand for `lives = lives - 1`)

### Step 11: Show the Current Game State

```python
# Show the current state of the word
print("Your word:", " ".join(guessed_word))
print(f"Lives left: {lives}")
```

**🤔 What's happening here?**
- We show the player the updated word with any correctly guessed letters
- `" ".join(guessed_word)` adds spaces between the letters/underscores for better readability
- `f"Lives left: {lives}"` is an f-string (formatted string) that lets us include the variable `lives` inside our text

### Step 12: Check If the Game is Over

```python
# After the loop ends, check why it ended
if "_" not in guessed_word:
    print("\n🎉 YOU WIN! You've guessed the word correctly!")
else:
    print("\n😢 GAME OVER! You ran out of lives.")
    print(f"The secret word was: {secret_word}")
```

**🤔 What's happening here?**
- This code runs after the main game loop ends
- `if "_" not in guessed_word:` checks if all letters have been guessed (no underscores left)
- If there are no underscores, the player has won!
- Otherwise, the loop must have ended because `lives` reached 0, so the player lost
- We reveal the secret word using an f-string

---

## 🚀 PART 3: MAKING OUR GAME AWESOME

### Step 13: Prevent Repeated Guesses

Let's add a feature to prevent players from guessing the same letter twice:

```python
# Create a list to store all guessed letters
guessed_letters = []

# Inside the main game loop:
if guess in guessed_letters:
    print("⚠️ You already guessed that letter! Try another one.")
    continue  # Skip the rest of the loop and start again
    
guessed_letters.append(guess)  # Add the current guess to our list
```

**🤔 What's happening here?**
- We create an empty list called `guessed_letters` to track all guesses
- `if guess in guessed_letters:` checks if the current guess is already in that list
- `continue` is a special command that skips the rest of the loop and starts the next iteration
- `guessed_letters.append(guess)` adds the current guess to our tracking list

### Step 14: Add Visual Feedback with ASCII Art

Let's add some cool visuals to show how many lives are left:

```python
# Hangman stages - from worst to best
stages = [
    '''
    +---+
    |   |
    O   |
   /|\  |
   / \  |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|\  |
   /    |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|\  |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|   |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
    |   |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
        |
        |
       ===
    ''',
    '''
    +---+
    |   |
        |
        |
        |
       ===
    '''
]

# Inside the main game loop, replace "Lives left: {lives}" with:
print(stages[lives])
```

**🤔 What's happening here?**
- We created a list called `stages` with 7 different ASCII art drawings (6 lives + game over state)
- Each drawing is a multi-line string using triple quotes `'''`
- `stages[lives]` shows the drawing that corresponds to the current number of lives
- As `lives` decreases, we show a more complete hangman drawing

### Step 15: Add Word Categories

Let's organize our words into categories to make the game more interesting:

```python
# Word categories
categories = {
    "food": ["pizza", "burger", "sushi", "chocolate", "banana"],
    "animals": ["elephant", "penguin", "dolphin", "tiger", "giraffe"],
    "tech": ["python", "laptop", "keyboard", "internet", "coding"]
}

# Pick a random category
category = random.choice(list(categories.keys()))

# Pick a random word from that category
word_list = categories[category]
secret_word = random.choice(word_list)

# Tell the player the category
print(f"CATEGORY: {category.upper()}")
```

**🤔 What's happening here?**
- We created a **dictionary** called `categories` where:
  - The **keys** are the category names (food, animals, tech)
  - The **values** are lists of words that belong to each category
- `list(categories.keys())` gets all the category names
- `random.choice()` picks a random category
- `categories[category]` gets the list of words for that category
- Then we pick a random word from that specific category
- We tell the player which category their word belongs to as a hint

---

## 🏁 PUTTING IT ALL TOGETHER: THE COMPLETE GAME

Here's our complete Hangman game with all the features we've learned:

```python
import random

# Hangman ASCII art stages (from worst to best)
stages = [
    '''
    +---+
    |   |
    O   |
   /|\  |
   / \  |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|\  |
   /    |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|\  |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
   /|   |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
    |   |
        |
       ===
    ''',
    '''
    +---+
    |   |
    O   |
        |
        |
       ===
    ''',
    '''
    +---+
    |   |
        |
        |
        |
       ===
    '''
]

# Word categories
categories = {
    "food": ["pizza", "burger", "sushi", "chocolate", "banana"],
    "animals": ["elephant", "penguin", "dolphin", "tiger", "giraffe"],
    "tech": ["python", "laptop", "keyboard", "internet", "coding"]
}

# Game setup
def setup_game():
    print("🎮 WELCOME TO HANGMAN! 🎮")
    print("Try to guess the secret word one letter at a time.")
    print("But be careful - you only get 6 wrong guesses!")
    
    # Pick a random category
    category = random.choice(list(categories.keys()))
    
    # Pick a random word from that category
    word_list = categories[category]
    secret_word = random.choice(word_list)
    
    # Create blank spaces for each letter
    guessed_word = ["_"] * len(secret_word)
    
    # Set initial lives
    lives = 6
    
    # Create empty list for tracking guesses
    guessed_letters = []
    
    # Tell the player the category
    print(f"\nCATEGORY: {category.upper()}")
    print("Your word:", " ".join(guessed_word))
    print(stages[lives])
    
    return secret_word, guessed_word, lives, guessed_letters

# Main game function
def play_hangman():
    # Set up the game
    secret_word, guessed_word, lives, guessed_letters = setup_game()
    
    # Main game loop - runs until player wins or loses
    while lives > 0 and "_" in guessed_word:
        # Get player's guess
        guess = input("\nGuess a letter: ").lower()
        
        # Check if input is valid (single letter)
        if len(guess) != 1 or not guess.isalpha():
            print("❌ Please enter a single letter!")
            continue
        
        # Check if letter was already guessed
        if guess in guessed_letters:
            print("⚠️ You already guessed that letter! Try another one.")
            continue
        
        # Add guess to tracking list
        guessed_letters.append(guess)
        
        # Check if guess is correct
        if guess in secret_word:
            print("🎯 Good guess! That letter is in the word!")
            
            # Update all matching letters
            for index, letter in enumerate(secret_word):
                if letter == guess:
                    guessed_word[index] = guess
        else:
            print("❌ Oops! That letter is not in the word!")
            lives -= 1  # Lose a life
        
        # Show current game state
        print("Your word:", " ".join(guessed_word))
        print(f"Guessed letters: {', '.join(guessed_letters)}")
        print(stages[lives])
    
    # Game over - check result
    if "_" not in guessed_word:
        print("\n🎉 YOU WIN! You've guessed the word correctly!")
        print(f"The word was: {secret_word}")
    else:
        print("\n😢 GAME OVER! You ran out of lives.")
        print(f"The secret word was: {secret_word}")

# Start the game
play_hangman()

# Ask if player wants to play again
while input("\nPlay again? (y/n): ").lower() == 'y':
    play_hangman()

print("Thanks for playing! Bye! 👋")
```

## 🎯 COOL THINGS TO TRY NEXT

Now that you've built your Hangman game, here are some awesome ways to make it even better:

1. **Add a score system** - Give points for each correct guess!
2. **Add difficulty levels** - Easy (more lives), Medium, Hard (fewer lives)
3. **Add a timer** - Can you guess the word before time runs out?
4. **Add sound effects** - Play sounds for correct and wrong guesses
5. **Add multiplayer** - Let a friend choose the word instead of the computer
6. **Add more word categories** - Movies, sports, countries, etc.
7. **Create a leaderboard** - Save the highest scores in a file

## 🧠 WHAT YOU'VE LEARNED

Congrats! You've just built a complete game and learned some serious coding skills:

✅ **Variables** - Storing and tracking game information
✅ **Lists** - Keeping collections of related items
✅ **Dictionaries** - Organizing data with key-value pairs
✅ **Loops** - Repeating actions until conditions are met
✅ **Conditionals** - Making decisions based on player input
✅ **Functions** - Organizing code into reusable blocks
✅ **String manipulation** - Working with text in various ways

You're now well on your way to becoming an awesome coder! What will you build next? 🚀

---

## 🎨 GLOSSARY OF PYTHON CONCEPTS

- **Variable**: A container for storing data values
- **String**: A sequence of characters (text)
- **List**: An ordered collection of items
- **Dictionary**: A collection of key-value pairs
- **Loop**: Code that repeats until a condition is met
- **Conditional**: Code that makes decisions (if/else)
- **Function**: A reusable block of code
- **Module**: A file containing Python code that can be imported
- **Comment**: Text that Python ignores (starts with #)

---

## 👏 YOU DID IT!

Remember: Every amazing game developer started exactly where you are now. Keep practicing, keep building, and keep having fun with code! 🎮
