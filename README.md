import java.util.ArrayList;//importig array  list and scanner
import java.util.Scanner;


public class Hangman {
    public static void main(String[] args) {
        String word = "example";


        Scanner scanner = new Scanner(System.in);//creating scanner object
       
        int wrongGuesses = 0;//the amount of wrong guesses
        ArrayList<Character> wordState = new ArrayList<>();//creating array list to store the word
        for(int i = 0; i <word.length(); i++) {
           wordState.add('_');//if i is less than the length of the word add _ to the array list
           System.out.print(wordState.get(i));
        }
        System.out.println(" ");//welcoming message
        System.out.println("#########################");
        System.out.println("Welcome to Java Hangman!");
        System.out.println("#########################");
       
        System.out.println("Word:");


        for (char c : wordState) {//for every character in the word state c + a space will be printed
            System.out.print(c + " ");//making every character have a space in between and be on the same line and taking only the 1st character of the input if the user decides to type a word instead of a letter
           
        }
        System.out.println("");//skipping a line


        System.out.println("Guess a letter:");
        char guess = scanner.next().toLowerCase().charAt(0);//allowing user to input a letter and making the letter lowercase so that its easier to recognize for the program
     


        if(word.indexOf(guess) >= 0) {//if the first occurance of guessed letter is in the word then the index will be 0 or higher
           System.out.println("Correct guess!");


           for(int i = 0; i < word.length(); i++) {
              if(word.charAt(i) == guess) {//i is the character of the word and if that character is = to the guessed letter then the letter will be added to the arraylist at the right index
                 wordState.set(i, guess);//if the guess is right it sets the guessed letter in the arraylist
              }
           }
        }
        else {
           wrongGuesses++;//if there is a wrong guess the amount of wrong guesses increases by 1
           System.out.println("Wrong guess! Total wrong guesses: " + wrongGuesses);//shows the amount of wrong guesses
        }
        scanner.close();
    }
    static String getHandmanArt(int wrongGuesses) { //creating a method to get the hangman art if a guess is wrong
       return switch(wrongGuesses){//Ascii art for hangman 
case 0 -> """
       






        """;
case 1 -> """
        O
   


        """;
case 2 -> """
        0
        |
       
        """;
case 3 -> """
        0
       /|
       
        """;
        case 4 -> """
        0
       /|\
       
        """;
         case 5 -> """
        0
       /|\
       /
        """;
         case 6 -> """
        0
       /|\
       / \
        """;
        default -> "";
       };
    }
}

