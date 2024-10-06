# Ping Pong Game

Welcome to the **Ping Pong Game** repository! This is a simple two-player game implemented on an LCD screen using an Arduino. Players control paddles to hit a ball back and forth, keeping score as they play.

## Table of Contents

- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Setup Project](#setup-project)
- [How to Play](#how-to-play)
- [Final Result](#final-result)

## Features

- Two-player mode
- Real-time score display
- Paddle and ball movement
- Simple and intuitive controls


### Hardware Requirements

![th](https://github.com/user-attachments/assets/428e49b1-f9be-49c0-976a-6c6fe7bc406d)
 - An Arduino board (e.g., Arduino Uno)
   
![th](https://github.com/user-attachments/assets/be68ad8b-f8ef-41b8-8093-b0128e9f9562)
- Push buttons for player controls
  
![th](https://github.com/user-attachments/assets/4c1e45e5-e678-459d-bca2-6d8267862e7a)
- A breadboard (optional)
  
![th](https://github.com/user-attachments/assets/e898790c-3443-4566-81c8-fdef19c2efcb)
- Jumper wires
  
![th](https://github.com/user-attachments/assets/4fe8ce4b-0ecd-4b07-a087-75293052f2ef)
- A Liquid Crystal Display (LCD) with I2C interface

## Setup Project
![c](https://github.com/user-attachments/assets/1b9c22eb-99d5-4c27-9628-3d7eca2b9dbb)

In this project, the hardware setup consists of an Arduino Uno connected to a Liquid Crystal Display (LCD) and a breadboard. The Arduino serves as the central controller, handling input from buttons for player controls while updating the LCD with the game state and score.

## How to Play
Game Objective
The objective of the game is to score points by getting the ball past your opponent's paddle. Players control their paddles to hit the ball back and forth, trying to prevent the ball from reaching their side of the screen.

Controls:
- Player 1 Controls:
  
-> Move Up: Press the button connected to pin 5.

-> Move Down: Press the button connected to pin 10.

- Player 2 Controls:
  
-> Move Up: Press the button connected to pin 2.

-> Move Down: Press the button connected to pin 3.

- Scoring :
  
-> Each player scores a point when the opponent fails to return the ball and it goes off the edge of their side of the screen.

-> The score is displayed at the top of the LCD screen.

- Winning the Game:
  
-> The game continues until a predetermined score is reached (e.g., 5 or 10 points).

-> The player who first reaches the target score is declared the winner.

- Gameplay Tips:
  
-> Keep an eye on the ball's direction to anticipate its movement.

-> Use quick reflexes to position your paddle in the right spot to return the ball effectively.

-> Practice makes perfect—familiarize yourself with the controls for better performance!


## Final result
![image](https://github.com/user-attachments/assets/467c4840-b877-42b4-8086-5e83d5f43f1f)

