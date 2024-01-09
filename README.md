# Blackjack Game

A simple console-based implementation of the classic Blackjack card game in Python.

## Rules

- The goal is to beat the computer's score without going over 21.
- Face cards (Jack, Queen, King) have a value of 10.
- Aces can be counted as 1 or 11, depending on which value is more beneficial.
- The game ends when the player decides to pass or exceeds 21.

## How to Play

1. Run the program.
2. You'll be dealt two cards initially.
3. Choose to get another card ('y') or pass ('n').
4. Try to build a hand with a total value closer to 21 than the computer.

## Code Structure

- `deal_card()`: Function to randomly select a card from the deck.
- `calculation_score(cards)`: Function to calculate the total score of a hand.
- `compare(user_score, computer_score)`: Function to compare the player's and computer's scores.
- `play_game()`: Main function to initiate and control the game.

## Usage

1. Run the Python script in a console or terminal.
2. Follow the prompts to play the game.
3. Enjoy the game of Blackjack!

## Example

```python
cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
import random
from replit import clear


def deal_card():
  return random.choice(cards)


def calculation_score(cards):
  if sum(cards) == 21 and len(cards) == 2:
    return 0
  if 11 in cards and sum(cards) > 21:
    cards.remove(11)
    cards.append(1)
  return sum(cards)


"""take a list of cards and return the score calculated from the cards"""


def compare(user_score, computer_score):
  if user_score == computer_score:
    return "Draw"
  elif computer_score == 0:
    return "Lose, opponent has Blackjack"
  elif user_score == 0:
    return "Win with a Blackjack"
  elif user_score > 21:
    return "You went over. You lose"
  elif computer_score > 21:
    return "Opponent went over. You win"
  elif user_score > computer_score:
    return "You win"
  else:
    return "You lose"


def play_game():
  print(logo)

  user_cards = []
  computer_cards = []
  is_game_over = False

  for _ in range(2):
    user_cards.append(deal_card())
    computer_cards.append(deal_card())

  while not is_game_over:
    user_score = calculation_score(user_cards)
    computer_score = calculation_score(computer_cards)
    print(f"Your cards: {user_cards}, current score: {user_score}")
    print(f"Computer's first card: {computer_cards[0]}")

    if user_score == 0 or computer_score == 0 or user_score > 21:
      is_game_over = True
    else:
      user_should_deal = input(
          "Type 'y' to get another card, type 'n' to pass: ")
      if user_should_deal == "y":
        user_cards.append(deal_card())
      else:
        is_game_over = True

  while computer_score != 0 and computer_score < 17:
    computer_cards.append(deal_card())
    computer_score = calculation_score(computer_cards)

  print(f"Your final hand: {user_cards}, final score: {user_score}")
  print(f"Computer's final hand: {computer_cards}, final score: {computer_score}")
  print(compare(user_score, computer_score)
while input("Do you want to play a game of Blackjack? Type 'y' or 'n': "):
  clear()
  play_game()
