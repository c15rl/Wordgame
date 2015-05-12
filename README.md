# Wordgame
CS1 assignment (Dalton)
import java.util.Scanner;

import org.dalton.cs1.RandomWord;

/*Author-Raina Lopez
 * Bonuses: Keeps score
 * Known Errors: N/A
 * Logs: Added more documentation 5/30/2012
 */

public class wordgame {
	public static void main(String[] args) {

	
		//declare variables
		String user = "";	//user
		Scanner input = new Scanner(System.in);	//user's input
		boolean correct = false;
		int guess = 1;
		boolean playgame = true;
		int wins = 0;
		int loss = 0;

		while (playgame == true)
		{
			//word related variables
			RandomWord rw = new RandomWord();
			String myword = (rw.getWord());
			String mydef =("definition: (" + rw.getPartOfSpeech()+") " + rw.getDefinition());
			String sentence = ("example: " +rw.getExample());

			correct = false;
			while (correct == false)
			{	
				System.out.println("You have three chances to guess the word.\r" + mydef + "\r" + sentence);

				while (guess < 4)	//3 tries to get the correct word
				{
					System.out.println("This is guess " + guess);
					user = input.nextLine();

					if (user.equalsIgnoreCase (myword))	//if user is correct
					{
						System.out.println("That was correct.");
						guess = 4;
						correct = true;
						wins++;	//keeping score
					}
					else					//if user is incorrect
					{
						System.out.println("That was incorrect.");
						guess++;
						correct = false;
						if (guess == 4 )
						{
							guess = 4;
							correct = true;
							loss++; //keeping score
						}
					}

				}//if the word you guess is...
				if (guess == 4);
				System.out.println("The word was: " + myword);	//shows word at the end of the game
				{
					if (user.equalsIgnoreCase (myword))		//says that user wins
					{
						System.out.println("You Win");

					}
					else									//says that user loses
					{
						System.out.println("You Lose");

					}
					System.out.println("do you want to play again. type y or n");	//play again
					user = input.nextLine();
					if (user.equalsIgnoreCase("n"))		//if not
					{
						playgame = false;
						System.out.println("You won " + wins + " times. You lost " + loss + " times.");	//print score
					}
					else if (user.equalsIgnoreCase("y"))			//continue game & continue keeping score
					{
						guess = 1;
						playgame = true;
					}
						
					
				}//finding the winner or loser

			}//end of actual game	
		}//while
	}//program
} //main
