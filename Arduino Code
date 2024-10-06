// Developed by Zaid ZBAKH

#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Pin definitions for I2C
#define SDA A4
#define SCL A5

// Button definitions for player controls
#define Joueur_1_bouton_bas 10   // Player 1 down button
#define Joueur_1_bouton_haut 5    // Player 1 up button
#define Joueur_2_bouton_bas  2    // Player 2 down button
#define Joueur_2_bouton_haut 3     // Player 2 up button

// LCD configurations
#define LCD_ADDRESS 0x27 
#define LCD_COLUMNS 20
#define LCD_ROWS 4

// Game settings
#define PADDLE_SIZE 1      // Size of the paddles
#define BALL_SIZE 0.5      // Size of the ball
#define PADDLE_SPEED 1     // Paddle movement speed
#define BALL_SPEED 1.5     // Ball movement speed

// Game state variables
int paddle1Position = 0; 
int paddle2Position = 0; 
int ballPositionX = 0; 
int ballPositionY = 0; 
int ballDirectionX = BALL_SPEED; 
int ballDirectionY = BALL_SPEED; 
int player1Score = 0; 
int player2Score = 0;

// Initialize the LCD
LiquidCrystal_I2C lcd(LCD_ADDRESS, LCD_COLUMNS, LCD_ROWS);

void setup() {
  // Initialize the LCD and turn on the backlight
  lcd.begin(LCD_COLUMNS, LCD_ROWS);
  lcd.backlight();

  // Set button pins as inputs with internal pull-up resistors
  pinMode(Joueur_1_bouton_haut, INPUT_PULLUP);
  pinMode(Joueur_1_bouton_bas, INPUT_PULLUP);
  pinMode(Joueur_2_bouton_haut, INPUT_PULLUP);
  pinMode(Joueur_2_bouton_bas, INPUT_PULLUP);
}

void loop() {
  // Update the paddles and the ball positions
  updatePaddles();
  updateBall();

  // Clear the LCD for the new frame
  lcd.clear();

  // Draw paddles and ball on the LCD
  drawPaddles();
  drawBall();

  // Update the score display on the LCD
  updateScoreDisplay();

  // Delay for frame rate control
  delay(150);
}

// Function to move Player 1's paddle up
void MovePaddleUp() {
  if (paddle1Position != 0) {
    paddle1Position -= PADDLE_SPEED;
  }
}

// Function to move Player 2's paddle up
void movepaddle2() {
  if (paddle2Position != 0) {
    paddle2Position -= PADDLE_SPEED;
  }
}

// Function to move Player 2's paddle down
void movepaddledown2() {
  if (paddle2Position != (LCD_ROWS - PADDLE_SIZE)) {
    paddle2Position += PADDLE_SPEED;
  }
}

// Function to move Player 1's paddle down
void MovePaddleDown() {
  if (paddle1Position != (LCD_ROWS - PADDLE_SIZE)) {
    paddle1Position += PADDLE_SPEED;
  }
}

// Function to update the paddle positions based on button inputs
void updatePaddles() {
  // Player 1 controls
  if (digitalRead(Joueur_1_bouton_haut) == HIGH) {
    MovePaddleUp();
  } else if (digitalRead(Joueur_1_bouton_bas) == HIGH) {
    MovePaddleDown();
  }

  // Player 2 controls
  if (digitalRead(Joueur_2_bouton_haut) == HIGH) {
    movepaddle2();
  } else if (digitalRead(Joueur_2_bouton_bas) == HIGH) {
    movepaddledown2();
  }

  // Constrain paddle positions to stay within bounds
  paddle1Position = constrain(paddle1Position, 0, LCD_ROWS - PADDLE_SIZE);
  paddle2Position = constrain(paddle2Position, 0, LCD_ROWS - PADDLE_SIZE);
}

// Function to update the ball position and check for collisions
void updateBall() {
  // Move the ball
  ballPositionX += ballDirectionX;
  ballPositionY += ballDirectionY;

  // Check for paddle collisions
  if (ballPositionX == 1 && ballPositionY >= paddle1Position && ballPositionY <= paddle1Position + PADDLE_SIZE) {
    ballDirectionX = BALL_SPEED; // Ball hits Player 1's paddle
  } else if (ballPositionX == LCD_COLUMNS - BALL_SIZE - 1 && ballPositionY >= paddle2Position && ballPositionY <= paddle2Position + PADDLE_SIZE) {
    ballDirectionX = -BALL_SPEED; // Ball hits Player 2's paddle
  }

  // Check for out of bounds and update score
  if (ballPositionX <= 0 || ballPositionX >= LCD_COLUMNS - BALL_SIZE) {
    if (ballPositionX <= 0) {
      player2Score++; // Player 1 missed, Player 2 scores
    } else {
      player1Score++; // Player 2 missed, Player 1 scores
    }
    ballDirectionX = -ballDirectionX; // Reverse ball direction
  }

  // Check for top and bottom wall collisions
  if (ballPositionY <= 0 || ballPositionY >= LCD_ROWS - BALL_SIZE) {
    ballDirectionY = -ballDirectionY; // Reverse ball direction
  }
}

// Function to draw paddles on the LCD
void drawPaddles() {
  // Draw Player 1's paddle
  for (int i = 0; i < PADDLE_SIZE; i++) {
    lcd.setCursor(0, paddle1Position + i);
    lcd.write(byte(255)); // Custom character for the paddle
  }

  // Draw Player 2's paddle
  for (int i = 0; i < PADDLE_SIZE; i++) {
    lcd.setCursor(LCD_COLUMNS - 1, paddle2Position + i);
    lcd.write(byte(255)); // Custom character for the paddle
  }
}

// Function to draw the ball on the LCD
void drawBall() {
  lcd.setCursor(ballPositionX, ballPositionY);
  lcd.write(byte(255)); // Custom character for the ball
}

// Function to update and display the score on the LCD
void updateScoreDisplay() {
  lcd.setCursor(LCD_COLUMNS / 2 - 2, 0); // Set cursor to the center for Player 1's score
  lcd.print(player1Score);
  lcd.setCursor(LCD_COLUMNS / 2 + 1, 0); // Set cursor to the center for Player 2's score
  lcd.print(player2Score);
}
