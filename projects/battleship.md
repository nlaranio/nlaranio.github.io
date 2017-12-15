---
layout: project
type: project
image: images/Battleship.png
title: Battleship
permalink: projects/battleship
date: 2016
labels:
 - Battleship game
 - Java games
 - EZJava
 - Learning Java
summary: A java application to play the game Battleship
---

### Table of contents

* [Overview: Battleship](#overview-of-battleship)
* [My Role](#my-role)
* [Install](#install)

#### Overview of Battleship
This battlship game is a Java program based on the board game of the same name. The game as it is supports 2 players taking turns on 1 screen. Players start by placing their ships and then take turns marking spots on a grid to try and hit all of the opponents ships. It was built as a group project in ICS111. It runs on the EZJava framework that was a core component of that class; you can find more about that [here](http://www2.hawaii.edu/~dylank/ics111/).

#### My Role
My role in the group was to develop the grid and all of its assets;
<ul>
 <li>GameBoard object and methods</li>
 <li>Cursor for placing and marking the grid</li>
 <li>Ship object and placement</li>
 <li>Game states such as; hit, miss, win</li>
 <li>Main menu</li>
</ul>  

Our pre development design
<img src="/images/Battleship-Game.png">

![b](/images/Battleship-Game.png)

My source code for the board.
```
public class BattleshipBoard{

	//-------------MEMEBER VARIABLES--------------
	
	
	protected Cell[][] Board; //2D array of cells that act as game board
	
	protected int Xpos; //grid x begin
	
	protected int Ypos; //grid y begin
	
	protected int Size; //size of grid
	
	protected int Spacing; //spacing/sizeof cells (in pixels)

	ArrayList<EZImage> Markers; //array list of images for the markers on the board

	//-------------CONSTRUCTORS--------------
	
	public BattleshipBoard(int xpos,int ypos,int size, int spacing){
		Xpos = xpos; //xpos start x of board
		Ypos = ypos; //ypos start y of board
		Size = size; //size of the board; size x size
		Spacing = spacing; //spacing of the cells; each would be "spacing" pixels
		Board = new Cell[Size][Size]; //initialize size x size array
		Markers = new ArrayList<EZImage>();
		
		for(int i = 0;i < Size;i++){ //for loop that fills 2D cell array
			for(int j = 0;j < Size;j++)
				Board[i][j] = new Cell(Xpos + i*Spacing, Ypos + j*Spacing); //spaces out each cell by spacing x i
		}
	}
	
	//---------------METHODS------------------

	//hides all cell markers
	public void hideMarkers(){
		for(int i = 0;i < Size;i++){
			for(int j = 0;j < Size;j++){
				Board[i][j].hideMarker();
			}
		}
	}
	
	//shows all cell markers
	public void showMarkers(){
		for(int i = 0;i < Size;i++){
			for(int j = 0;j < Size;j++){
				Board[i][j].showMarker();
			}
		}
	}

	//--------------ACCESSORS----------------
	
	//returns grid top left xpos
	public int getXpos(){
		return Xpos;
	}
	
	//returns grid top left ypos
	public int getYpos(){
		return Ypos;
	}
	
	//returns spacing of cells
	public int getSpacing(){
		return Spacing;
	}
	
	//returns size of grid (size x size)
	public int getSize(){
		return Size;
	}
	
	//returns the x position of the cell image
	public int getCellImgX(int indexX, int indexY){
		return Board[indexX][indexY].getCellImgX();
	}
	
	//returns the y position of the cell image
	public int getCellImgY(int indexX, int indexY){
		return Board[indexX][indexY].getCellImgY();
	}




}//END BOARD

/* Cell class that stores the data and visual representation of each cell of the gameboard
*
*/

class Cell{
	
	EZImage Img; //cell image
	
	EZImage Marker; //marker on the cell(red for hit, white for miss)
	
	boolean Attacked; //holds if the ship has been attacked
	
	boolean Hit; //if a ship on this position was hit
	
	//-----CONSTRUCTORS-----
	Cell(int xpos,int ypos){
		Img = EZ.addImage("Cell.png", xpos, ypos); //add cell img
		Marker = EZ.addImage("Empty.png", xpos, ypos); //initialize empty img
		Attacked = false; //start not attacked
		Hit = false; //start not hit
	}
	
	//------METHODS------
	
	//attack the cell if its filled then Hit becomes true
	boolean attack(boolean hit){
		if(Attacked){
			return false; // if false is returned that means its already been attacked
		}else{
			Attacked = true; //make Attacked true
			Hit = hit; //set Hit equal to hit which you get from Ships;
			placeMarker(); //place marker
			return true; //return true; the cell is attacked
		}
	}
	
	//places marker at cell position based on state
	void placeMarker(){
		if(Attacked && !Hit)// attacked but no ship hit; miss marker
			Marker = EZ.addImage("Miss.png", Img.getXCenter(), Img.getYCenter());
		else if(Attacked && Hit) //attacked and hit; hit marker
			Marker = EZ.addImage("Hit.png", Img.getXCenter(), Img.getYCenter());
	}
	
	//hides the marker image
	void hideMarker(){
		Marker.hide();
	}
	
	//shows the marker image
	void showMarker(){
		Marker.show();
	}
	
	//hides the cell img
	void hideCell(){
		Img.hide();
	}
	
	//shows the cell img
	void showCell(){
		Img.show();
	}
	
	//-------ACCESSORS------
	
	
	//returns Attacked
	boolean getAttacked(){
		return Attacked; 
	}
	
	//returns Hit
	boolean getHit(){
		return Hit;
	}
	
	//returns state of Attacked and Hit in binary state form
	int getState(){
		if(!Attacked && !Hit)
			return 00; //no marker state; not attacked
		else if(Attacked && !Hit) 
			return 10; //white marker state; attacked but no ship hit
		else if(Attacked && Hit)
			return 11; //red marker state; attacked and ship hit
		else
			return 01; // something went wrong if we are in this state
	}
	
	//returns center of the cell x
	int getCellImgX(){
		return Img.getXCenter();
	}
	
	//returns center of the cell y
	int getCellImgY(){
		return Img.getYCenter();
	}
	
 }//END Cell
```


[Battleship](https://drive.google.com/open?id=1O6GzvBqtqb3qP90XlbRyO4JCSx5FweIa)
