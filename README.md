package com.byaj;

import java.math.RoundingMode; import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner readability = new Scanner(System.in);
        System.out.println("Text: ");
        String text = readability.nextLine();

        int countLetter = 0;
        int countwords = 1;


        for (int i = 0; i < text.length(); i++) {
            if (Character.isLetter(text.charAt(i)))
                countLetter++;
        }

        for (int i = 0; i < text.length() - 1; i++) {
            if ((text.charAt(i) == ' ') && (text.charAt(i + 1) != ' ')) {
                countwords++;
            }
        }
        int countsentences = text.split("[!?.:]+").length;

        System.out.println(countsentences + " Sentences");
        System.out.println(countLetter + " letters.");
        System.out.println(countwords + " Words");


        float L = 1.0f * countLetter / countwords * 100;
        float S = 1.0f * countsentences / countwords * 100;

        int grade = (int) Math.round(0.0588 * L - 0.296 * S - 15.8);

        if (grade < 1) {
            System.out.println("Before Grade 1");
        }
        else if (grade >= 16)
            System.out.println("Grade 16+");
        else
            System.out.println("Grade: " + grade);

    }
}
