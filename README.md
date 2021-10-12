import java.util.Arrays;
import java.util.Locale;
import java.util.Scanner;

public class ArrayTools {


    public static void main(String[] args) {
        options();
    }

    static void options(){
        String[] array = new String[0];
        Scanner console = new Scanner(System.in);
        System.out.print("1. Ceaser Cipher Encryption \n");
        System.out.print("2. Array Operations Average, Contains, Reverse \n");
        System.out.print("Please Enter the option to perform the operation \n");
        String message = console.nextLine();
        int option = Integer.parseInt(message);
        switch (option) {
                case 1:
                    System.out.println("Initiating Ceaser Cipher Encryption");
                    System.out.println("Please Enter Message to be Encrypted");
                    String EncryptMessage = console.nextLine();
                    EncryptMessage = EncryptMessage.toLowerCase();
                    System.out.println("Please Enter the numeric Secret");
                    String EncryptKey = console.nextLine();
                    int EncryptSecret = Integer.parseInt(EncryptKey);
                    encodeCaesarCipher(EncryptMessage,EncryptSecret);
                    break;
                case 2:
                    System.out.println("Please Enter the Array of Integers seperated by space");
                    String inputArray = console.nextLine();
                    array = inputArray.split(" ");
                    ArrayAverage(array);
                    System.out.println("Please Enter the value to be searched");
                    String search = console.nextLine();
                    ArrayContains(array, search);
                    ArrayReverse(array);
                    break;
        }

    }

    public static void encodeCaesarCipher (String EncryptMessage, int EncryptSecret){
        StringBuilder sb = new StringBuilder();
        System.out.print("Encode Caesar Cipher Message is : ");
        for (int i = 0; i < EncryptMessage.length(); i++) {
            char c = EncryptMessage.charAt(i);
            if (c == ' ') {
                System.out.print(" ");
            } else {
                sb.append((char) (c + EncryptSecret));
            }
        }
        System.out.println(sb.toString());
        System.out.println("-- Decoding Caesar Cipher Message " + sb.toString()+ " with key " + EncryptSecret+"--");
        for (int i = 0; i < sb.length(); i++) {
            char c = sb.charAt(i);
            if (c == ' ') {
                System.out.print(" ");
            } else {
                System.out.print((char) (c - EncryptSecret));
            }
        }
        System.out.println();
        System.out.println("-----------------------------------------------------------");

        options();
    }
    public static void ArrayAverage(String[] InputArray){
        int result = 0;
        for(String str: InputArray) {
            result += Integer.parseInt(str);
        }
        System.out.println("Average of the Array is : "+ result/InputArray.length);
        System.out.println();
    }
    public static void ArrayContains(String[] InputArray, String search) {
        boolean found = false;
        for(String x : InputArray){
            if(x.equals(search)){
                found = true;
                break;
            }
        }
        System.out.println(found);
    }
    public static void ArrayReverse(String[] InputArray){
        int left = 0;
        int right = InputArray.length-1;
        while (left < right) {
            String temp = InputArray[left];
            InputArray[left] = InputArray[right];
            InputArray[right] = temp;
            left++;
            right--;
        }
        System.out.println("Reversed Array is ");
        System.out.print(Arrays.toString(InputArray));
        System.out.println();
        options();
    }
}
