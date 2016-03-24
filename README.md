# MakeyMakey.html
<html>
<head>
    <title>The Race</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.13/p5.js"></script>
    <script>
        var player1X;
        var player2X;
        var finishlineX;
        var levels = 0;
        var player1score = 0;
        var player2score = 0;

        function setup() {
            createCanvas(400, 400);
            player1X = 30;
            player2X = 30;
            finishlineX = width - 50;
        }

        function draw() {
            startGame();
            level();
            newLevel();
            scoreBoard()
        }

        function startGame() {
            background(123, 175, 212);
            strokeWeight(15);
            stroke(0);
            line(0, height / 2, width, height / 2) //Middle Line
            stroke(0);
            strokeWeight(10)
            line(finishlineX, 0, finishlineX, height) //Finish Line
            stroke(255);
            line(finishlineX - 10, 0, finishlineX - 10, height);
            stroke(0);
            line(60, 0, 60, height) //Start Line
            fill(0, 0, 255);
            strokeWeight(1);
            stroke(255);
            ellipse(player1X, height / 3, 50, 50);
            fill(255, 0, 0);
            ellipse(player2X, height / 1.5, 50, 50);
            noStroke();
            fill(255);
            textAlign(CENTER);
            textSize(12);
            text("Player 1", player1X, height / 3);
            text("Player 2", player2X, height / 1.5);
            fill(0);
            text("Player 1 is the right arrow", width / 2, 375);
            text("Player 2 is the left arrow", width / 2, 390);
            fill(255,0,0)
            textSize(30); 
            textAlign(CENTER); 
            text("Duel!!!", width / 2, 350); 
            
        }

        function newLevel() {
            if (player1X >= finishlineX) {
                noStroke()
                fill(255); //sets the color to red
                textSize(40); //makes the text larger
                textAlign(CENTER); //centers the text
                text("Player 1 Has Won!", width / 2, height / 2); //shows the text"Game Over"
                levels++;
                player1score++;
                player1X = constrain(player1X, 0, finishlineX);//constrains the player 1 from going over the finsih line
                player2X = constrain(player2X, 0, finishlineX - 1);//constrains the player 1 from going past the finsih line
                setup()//resets the game
                startGame();//resets the game
            }
            else if (player2X >= finishlineX) {
                noStroke()
                fill(255); //sets the color to red
                textSize(40); //makes the text larger
                textAlign(CENTER); //centers the text
                text("Player 2 Has Won!", width / 2, height / 2); //shows the text"Game Over"
                levels++;
                player2score++;
                player2X = constrain(player2X, 0, finishlineX);//constrains the player 2 from going over the finsih line
                player1X = constrain(player1X, 0, finishlineX - 10);//constrains the player 1 from going past the finsih line
                setup();//resets the game
                startGame();//resets the game
            }
        }

        function scoreBoard() {
            textSize(20) //makes the text larger
            textAlign(CENTER) //centers the text
            fill(0,0,255) //sets the color to blue
            text(player1score, width / 4.5, 60) //shows the user's score
            text("Player 1 Score:", width / 4.5, 25) //shows the word "Score"
            fill(255,0,0)//sets the color to red
            text(player2score, width / 1.25, 60) //shows the user's score
            text("Player 2 Score:", width / 1.25, 25) //shows the word "Score"
        }

        function keyPressed() {
            // frameRate(5)
            if (keyCode == RIGHT_ARROW) {//if the right arrow is pressed
                player1X += 5;//make player 1 move
            }

            if (keyCode == LEFT_ARROW) {//if the left arrow is pressed
                player2X += 5;//make player 2 move
            }
        }
        
        function level() {
            fill(255); //sets the color to white
            textSize(30); //makes the text larger
            textAlign(CENTER); //centers the text
            text(levels, width / 2, 60); // shows the levels
            text("Level:", width / 2, 25); // shows the word "Level:"
        }
    </script>
</head>

<body>

</body>

</html>
