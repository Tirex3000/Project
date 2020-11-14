package com.company;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;
import java.util.Scanner;
import java.util.stream.Collectors;




public class Main {
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {


        getInt();
    }
    enum RomanNumeral {
        I(1), IV(4), V(5), IX(9), X(10),
        XL(40), L(50), XC(90), C(100),
        CD(400), D(500), CM(900), M(1000);

        private int value;

        RomanNumeral(int value) {
            this.value = value;
        }

        public int getValue() {
            return value;
        }

        public static List<RomanNumeral> getReverseSortedValues() {
            return Arrays.stream(values())
                    .sorted(Comparator.comparing((RomanNumeral e) -> e.value).reversed())
                    .collect(Collectors.toList());
        }
    }
    public static String arabicToRoman(int number) {
        if ((number <= 0) || (number > 4000)) {
            throw new IllegalArgumentException(number + " is not in range (0,4000]");
        }

        List<RomanNumeral> romanNumerals = RomanNumeral.getReverseSortedValues();

        int i = 0;
        StringBuilder sb = new StringBuilder();

        while ((number > 0) && (i < romanNumerals.size())) {
            RomanNumeral currentSymbol = romanNumerals.get(i);
            if (currentSymbol.getValue() <= number) {
                sb.append(currentSymbol.name());
                number -= currentSymbol.getValue();
            } else {
                i++;
            }
        }

        return sb.toString();
    }

    public static void getInt() {
        System.out.print("Введите запрос:");
        String request;
        request = scanner.nextLine();

        int index = request.indexOf("+");
        if (index == -1) {
            index = request.indexOf('-');
        }
        if (index == -1) {
            index = request.indexOf("*");
        }
        if (index == -1) {
            index = request.indexOf("/");
        }
        char operation = request.charAt(index);

        if (request.length() >= 3 || request.length() <= 5) {
            String num1 = request.substring(0, index);
            String num2 = request.substring(index + 1, request.length());

            int a, b;
            try {
                int result;
                a = Integer.parseInt(num1);

                b = Integer.parseInt(num2);

                if ((a < 11 && a > 0) && (b < 11 && b > 0)) {
                    switch (operation) {
                        case '+':
                            result = a + b;
                            System.out.println("Результат = " + result);
                            break;
                        case '-':
                            result = a - b;
                            System.out.println("Результат = " + result);
                            break;
                        case '*':
                            result = a * b;
                            System.out.println("Результат = " + result);
                            break;
                        case '/':
                            result = a / b;
                            System.out.println("Результат = " + result);
                            break;
                        default:
                            System.out.println("Операция не распознана");
                    }
                } else {
                    System.out.println("Числа введены неверно!");
                }
            } catch (NumberFormatException e) {
                int aa = 0;
                int bb = 0;
                if (num1.equals("I")) {
                    aa = 1;
                } else if (num1.equals("II")) {
                    aa = 2;
                } else if (num1.equals("III")) {
                    aa = 3;
                } else if (num1.equals("IV")) {
                    aa = 4;
                } else if (num1.equals("V")) {
                    aa = 5;
                } else if (num1.equals("VI")) {
                    aa = 6;
                } else if (num1.equals("VII")) {
                    aa = 7;
                } else if (num1.equals("VIII")) {
                    aa = 8;
                } else if (num1.equals("IX")) {
                    aa = 9;
                } else if (num1.equals("X")) {
                    aa= 10;
                }else aa=-1;


                if (num2.equals("I")) {
                    bb = 1;
                } else if (num2.equals("II")) {
                    bb = 2;
                } else if (num2.equals("III")) {
                    bb = 3;
                } else if (num2.equals("IV")) {
                    bb = 4;
                } else if (num2.equals("V")) {
                    bb = 5;
                } else if (num2.equals("VI")) {
                    bb = 6;
                } else if (num2.equals("VII")) {
                    bb = 7;
                } else if (num2.equals("VIII")) {
                    bb = 8;
                } else if (num2.equals("IX")) {
                    bb = 9;
                } else if (num2.equals("X")) {
                    bb = 10;
                }else bb=-1;

                int result;
                String res;
                if (aa!=-1 && bb!=-1) {
                    switch (operation) {
                        case '+':
                            result = aa + bb;
                            res = Main.arabicToRoman(result);
                            System.out.println("Результат = " + res);
                            break;
                        case '-':
                            result = aa- bb;
                            res = Main.arabicToRoman(result);
                            System.out.println("Результат = " + res);

                            break;
                        case '*':
                            result = aa * bb;
                            res = Main.arabicToRoman(result);
                            System.out.println("Результат = " + res);
                            break;
                        case '/':
                            result = aa / bb;
                            res = Main.arabicToRoman(result);
                            System.out.println("Результат = " + res);
                            break;
                        default:
                            System.out.println("Операция не распознана");
                    }
                }else {
                    System.out.println("Операция не распознана");
                }
            }

        } else
            System.out.println("Неверный формат строки!");
    }
}


