# ICS3U1-isp-code
This is a java hangman game i has made for my grade 11 computer science final project worth 10 percent of my final mark


import java.util.ArrayList;
import java.util.Scanner;


public class Hangman {
    public static void main(String[] args) {
        String word = "example";


        Scanner scanner = new Scanner(System.in);
       
        int wrongGuesses = 0;
        ArrayList<Character> wordState = new ArrayList<>();
        for(int i = 0; i <word.length(); i++) {
           wordState.add('_');
           System.out.print(wordState.get(i));
        }
        System.out.println(" ");
        System.out.println("#########################");
        System.out.println("Welcome to Java Hangman!");
        System.out.println("#########################");
       
        System.out.println("Word:");


        for (char c : wordState) {
            System.out.print(c + " ");
           
        }
        System.out.println("");


        System.out.println("Guess a letter:");
        char guess = scanner.next().toLowerCase().charAt(0);
     


        if(word.indexOf(guess) >= 0) {
           System.out.println("Correct guess!");


           for(int i = 0; i < word.length(); i++) {
              if(word.charAt(i) == guess) {
                 wordState.set(i, guess);
              }
           }
        }
        else {
           wrongGuesses++;
           System.out.println("Wrong guess! Total wrong guesses: " + wrongGuesses);
        }
        scanner.close();
    }
    static String getHandmanArt(int wrongGuesses) {
       return switch(wrongGuesses){
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



