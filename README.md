# Pseudocode
Game development and problem solving project pseudocode and code on `unity` for remembrance
# Final Project
  
//Not used! ONLY FOR REFERENCE
//
- CONST int death = 0;
- CONST int retreat = 2;
- CONST int rifleFireHitEnemy = 1;                   // 1/5
- CONST int grenadeExplosion = 3;                //1/4
- CONST int rifleFireHitPlayer = 1;                //1/5
- CONST int knifeWound = 1;                       //1/3
- CONST knifeAmmo = 1;
- CONST knifeDistance = 10;
- CONST int rifleType1Ammo = 15;      //Autoreload
- CONST int rifleType2Ammo = 15;     //Must get ammo
- CONST rifleType1Distance = 100;
- CONST rifleType2Distance = 150;

  
// Consts


- CONST int truck = 800;
- CONST int crate = 400	
- CONST int explosion1=300;                 //1/10	
- CONST int explosion2=600;                 //1/10	
- CONST int explosion3=900;                 //1/10

  
// Variables


- int enemy1HP= 5;                      //random
- int enemy2HP= 5;                      //random
- int playerHP = 5;                     //random
- int grenadeAmmo = 3;
- int rifleAmmo = 15;
- int enemy1Ammo = 15;
- int enemy2Ammo= 15;
- bool enemy1Alive = true;
- bool enemy2Alive = true;
- bool playerAlive = true;
- bool hidden = false;
- bool mine1 = true;
- bool mine2 = true;
- bool mine3 = true;
- bool end = false;
- int enemy1Dest = 1000;                //1/10
- int enemy2Dest = 500;                  //1/3
- int playerDest = 100;                     //1
  
```
while (!end){
 death();
 	//if game not over
 	 if (enemy1Alive || enemy2Alive){
 	  playerSee();
  }if (enemy1Alive){
    enemy1See();
  }if (enemy2Alive){
    enemy2See();
  }
}
```
```
void death(){
	if (enemy1HP <= 0 && enemy2HP <=0 ){
		print(“PLAYER WINS”);
		end =true;
	}else if (playerHP <= 0){
		print(“ENEMIES WIN”);
		playerAlive = false;
		end =true;
	}else if (enemy1HP <=0){
		print(“ENEMY 1 DEAD”);
		enemy1Alive = false;
	}else if (enemy2HP f<=0){
		print(“ENEMY 2 DEAD”);
		enemy2Alive = false;
	}
}
```
```
void playerSee(){
	mine(playerDest, playerHP);
  int random = random(1,3);
	if (playerHP<3){
	  //Player retreats
	  playerDest -= 40;
	}if (random ==1){	
		//Player sees enemy
    if (playerHP >2){
  		playerDest +=20;
  	}if (rifleAmmo <=0){
  		if (playerDest- truck >0 && playerDest-truck <playerDest-crate){
  			//Player closer to truck. Move to left
  			playerDest-=20;
  		}if (playerDest- truck <0 && playerDest-truck <playerDest-crate){
  			//Player closer to truck. Move right
  			playerDest+=20;
  		}if (playerDest- crate>0 && playerDest-truck <playerDest-crate){
  			//Player closer to crate. Move to left
  			playerDest-=20;
  		}if (playerDest- crate<0 && playerDest-truck <playerDest-crate){
  			//Player closer to crate. Move right
  			playerDest+=20;
  		}
  	}if (enemy1Alive && playerDest - enemy1Dest <=150 && playerDest - enemy1Dest >= -150){
  		riflePlayer();
  	}if (enemy2Alive && playerDest - enemy2Dest <=150 && playerDest - enemy2Dest >= -150){
  		riflePlayer();
  	}if (if enemy1Alive && playerDest - enemy1Dest <=30 && playerDest - enemy1Dest >= -30 && grenadeAmmo != 0){
  		grenade(enemy1HP);
  	}if (enemy2Alive && playerDest - enemy2Dest <=30 && playerDest - enemy2Dest >= -30 && grenadeAmmo !=0){
  		grenade(enemy2HP);
  	}
  }if (playerDest == crate || playerDest == truck){
  	//player hiding
  	hidden = true;
  rifleAmmo = 15;
  }else{
  	hidden = false;
  }
}
```
```
void enemy1See(){
	mine(enemy1Dest,enemy1HP);
  int random1 = random(1,10);
  if (enemy1HP<3){
  	//Enemy1 retreats
  	enemy1Dest -= 40;
	}if (random1 ==1 && !hidden){
    //Enemy1 sees player
  if (enemy1HP >2){
  		enemy1Dest +=20;
  		}if (playerDest - enemy1Dest <=100 && playerDest - enemy1Dest >= -100){
  		rifleEnemy1(enemy1Ammo);
  	}if (playerDest - enemy1Dest <=10 && playerDest - enemy1Dest >= -10){
  		knife();
  	}
  }
}
```
```
void enemy2See(){
	mine(enemy2Dest,enemy2HP);	
  int random2 = random(1,3);
  if (enemy2HP <3){
	  //Enemy2 retreats
	  enemy2Dest -= 40;
	}if (random2 ==1) && !hidden{
    if (enemy2HP >2){
		  //Enemy2 sees player
		  enemy2Dest +=20;
  	}if (playerDest - enemy2Dest <=100 && playerDest - enemy2Dest >= -100){
  		rifleEnemy(enemy2Ammo);
  	}if (playerDest - enemy2Dest <=10 && playerDest - enemy2Dest >= -10){
  		knife();
  	}
  }
}
```
```
void grenade(int hp){
	int randomGrenade = random(1,4);
	if (randomGrenade == 1){
		//grenade goes off
		grenadeAmmo --;
		hp -=3;
	}
}
```
```
void knife(){
	int randomKnife = random(1,3);
	if (randomKnife == 1){
		//Knife hits
		playerHP --;
	}
}
```
```
void riflePlayer(){
	if (rifleAmmo >0 && !hidden){
		int randomShot = random(1,5);
		rifleAmmo --;
		if (randomShot ==1){
			hp --;
		}
	}
}
```
```
void rifleEnemy(int ammo){
	if (ammo >0){
		int randomShot1 = random(1,5);
		ammo--;
		if (randomShot1 ==1){
			playerHP--;
		}
	}else{
		//Enemy reloads
		ammo= 15;
	}
}
```
```
void mine(targetDest,targetHp){
	if (targetDest == explosion1 && mine1){
		mine1 = false;
		targetHp-=3;
	}if (targetDest == explosion2 && mine2){
		mine2 = false;
		targetHp-=3;
	}if (targetDest == explosion3 && mine3){
		mine3 = false;
		targetHp-=3;
	}
}
```


# Mario
- GameObject start = GameObject.Find(“Start”);
- GameObject mario = GameObject.Find(“Mario”);
- GameObject flag = GameObject.Find(“Flag”);
- GameObject win = GameObject.Find(“Win”);
- GameObject enemy = GameObject.Find(“Enemy”);
- GameObject gameOver = GameObject.Find(“GameOver”);
- GameObject fireFlower= GameObject.Find(“FireFlower”);
- GameObject mushroom= GameObject.Find(“Mushroom”);
- GameObject star= GameObject.Find(“Star”);
- GameObject coinBlock= GameObject.Find(“CoinBlock”);
- GameObject starBlock = GameObject.Find(“StarBlock”);
- GameObject fireBlock = GameObject.Find(“FireFlowerBlock”);
- GameObject mushroomBlock =GameObject.Find(“MushroomBlock”);
- GameObject fireball =GameObject.Find(“Fireball”);
- GameObject lifeMushroom = GameObject.Find(“ExtraLife”);
- GameObject pipe1=GameObject.Find(“Pipe1);
- GameObject pipe2= GameObject.Find(“Pipe2”);

```
gameOver.material=invisibleMaterial;
win.material=invisibleMaterial;
```
- int starConst = 1000000000000;
- int hp = 1;
- int coins = 0;
- int lives = 3;
- int flagX = flag.transform.position.x;
- int flagY = flag.transform.position.y;
- int marioX = mario.transform.position.x;
- int marioY = mario.transform.position.y;
- int marioZ = mario.transform.position.z;
- int enemyX = enemy.transform.position.x;
- int enemyY = enemy.transform.position.y;
- int pipeY = pipe1.transform.position.y;

- bool starMode = false;
- bool fireMode = false;
```
//Start game
void main(){
  if (start clicked){
	  start.material = invisibleMaterial;
    while (marioX <flagX){
      move();
      deathCheck();
      coins();
      mushroom();
	    flower();
	    star();
	    warp();
    }
  }if (mario.collision = greenMushroom.collision){
    lives++
    greenMushroom.setEnabled=false;
  }if (marioX >= flagX){
	  // game ends, display a game over sign across the board
	  win.material=defaultMaterial;
  }
}
```
```
//Keyboard actions for movement
void move(){
  if (NOT(mario.collision.gameObject.name == “Block”) || starMode){
    if (left arrow pushed down || “a” pushed down){
      // move mario left
      marioX-=2;
    }if (right arrow pushed down || “d” pushed down){
	    // move mario right
	    marioX+=2;
    }if ((up arrow pushed down || “w” pushed down || space pushed down) && mario.grounded){
      // move mario up;
      marioY+=2;
      WaitForSeconds(2);
    }
  }while (!mario.grounded){
    marioY- -;
  }
}
```
```
//Checks if mario fell off the map or if he hits an enemy. Changes lives and hp and allows for //game restart
void deathCheck(){
	if ((mario.collision == enemy.collision) || marioY <0){
		if (marioY-(mario.height/2) == enemyY+(enemy.height/2)){
			enemy.setEnabled(false);
		}else{
			hp = hp-1;
      if (hp ==0){
  	    lives = lives-1
  	    if (lives !=0){
  		    start.material = defaultMaterial;
  		    break;
  	    }else{
  			  //display game over sign and end game
  			  gameOver.material = defaultMaterial;
          break;
        }
		  }
	  }
  }
}
```
```
//If coin block hit, coin count increases and lives if coins reach 100.
void coins(){
if (mario.collision == coinBlock.collision && !mario.grounded){
		coins++
		if (coins ==100){
      coins = 0;
			lives++;
    }
	}
}
```
```
//Spawns mushroom and changes mario stats if mario and mushroom touch
void mushroom(){
if (mario.collision == mushroomBlock.collision && !mario.grounded){
		mushroom.setEnabled = true;
		if (mario.collision == mushroom.collision) {
		  mushroom.setEnabled = false;
		  mario.height= mario.height * 2;
		  hp =2;
		}
	}
}
```
```
// Spawns flower and changes mario stats if mario and flower touch
void flower(){
if (mario.collision == fireBlock.collision && !mario.grounded){
		fireFlower.setEnabled = true;
  if (mario.collision == fireflower.collision){
    mario.height= mario.height * 2;
    fireflower.setEnabled = false;
		fireMode=true;
		hp = 3;
		}if (fireMode && space pressed){
	    fireball = create(fireball);
	    fireball.transform.position = new Vector(marioX,marioY,marioZ)
	    fireball.shoot(player.direction());
    }
	}
}
````
```
//Spawns star and changes mario stats if mario and star touch
void star(){
	if (mario.collision == starBlock.collision && !mario.grounded){
		star.setEnabled=true;
    if (mario.collision == star.collision){
		  star.setEnabled = false;
		  hp=hp +starConst;
		  starMode =true;
		  WaitForSeconds(10);
		  hp =hp-starConst;
	  }
  }
}
```
```
void warp(){
	if (mario.collision == pipe1.collision){
    if (marioY == pipeY && (down arrow pressed || s pressed){
	  //teleport mario
	  marioX == pipe2;
    }



# Battleship

//object used as general term to describe any object. Anything happening to object refers to individual objects

// Objects, each object has size created. 
aircraftCarrier1;
aircraftCarrier2;
battleship1;
battleship2;
destroyer1;
destroyer2;
submarine1;
submarine2;
patrolBoat1;
patrolBoat2;
// board1 and board2 have width and height = 10
board1;
board2;
boardSize1= 100;
boardSize2= 100;

//ship is placeholder for actual ship name, used for simplicity in pseudocode
shipStatus1= True;
shipStatus2 = True;

nextButton; 

if object clicked && left arrow pushed then
	rotate object 90 degrees left
if object clicked && right arrow pushed then
	rotate object 90 degrees right
if (x position of object > x position of board 1 || x position of object < 0 || y position of object <0 || y position of object > y position of board1) then
	output “invalid placement. Place the piece elsewhere.”

if x position of object > x position of board1 || x position of object < 0  || y position of object <0 || y position of object > y position of board1) then
	output “invalid placement. Place the piece elsewhere.”

if all objects on board1 && nextButton clicked then
	next player’s turn. 

// board 2
if x position of object2 > x position of board 2 || x position of object2 < 0  || y position of object2 <0 || y position of object2 > y position of board2) then
	output “invalid placement. Place the piece elsewhere.”

if all objects on board2 && nextButton clicked then
	while all shipStatus1 != False then
	change camera position to focus on board1
	player1’s turn
	public int userRow1; 
	while (userRow1 <1 || userRow1 >10) then 
		public int userRow1;
	public int userColumn1;
	while (userColumn1<1 || userColumn1 >10) then
		public int userColumn1;
	int x1 = userRow1;
	int y1 = userColumn1;
	if (x1 touching part of object) && (y1 touching part of object) then
		change object color at x1 and y1 to blue
	else then
		change object color at x1 and y1 to red
	if object’s total coordinates hit then 
		shipStatus1 = False;
	while all shipStatus2 != False then
	change camera position to focus on board2
	player2’s turn
	public int userRow2; 
	while (userRow2 <1 || userRow2 >10) then 
		userRow2;
	public int userColumn2;
	while (userColumn2<1 || userColumn2 >10) then
		userColumn2;
	int x2 = userRow2;
	int y2 = userColumn2;
	if (x2 touching part of object) && (y2 touching part of object) then
		change object color at x2 and y2 to blue
	else then
		change object color at x2 and y2 to red
	if object’s total coordinates hit then 
		shipStatus2 = False;
	

print(“GAME OVER!”)
if any ship on board1 has shipStatus1 = True then
	print(“Player1 wins!”)
else then 
	print(“Player2 wins!”)

  }	
}
```

