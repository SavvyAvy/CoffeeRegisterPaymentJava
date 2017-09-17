//CoffeeRegisterPaymentJava
//Avrielle Rouse

import java.util.Scanner;

public class CoffeeShop
{
    static final double COFFEE = 3.25;
    static final double CREAM = 0.5;
    static final double SUGAR = 0.5;
    static final double TEA = 2.75;
    static final double ESPRESSO = 4.25;
    static final double SHOT_TWO =1.25;
    static double total = 0;
    static String receipt = "";
        
    public static void main(String[] args)
    {
        String startOrder = "";
        String orderAnotherLiquid = "";
      
        Scanner userInput = new Scanner(System.in);
        System.out.println("Hello and welcome to our coffee shop!");
        System.out.println();
        
        
        System.out.print("Would you like to place an order with us?\n" + 
                        "please enter Y for yes or N for no>> ");
        startOrder = userInput.next();
        System.out.println();
      
        while(startOrder.equals("Y") || startOrder.equals ("y"))
        {
          orderAnotherLiquid = "Y";
            while (orderAnotherLiquid.equals("Y") || orderAnotherLiquid.equals("y")) 
            {
                liquidMenu(userInput);
                System.out.println();
                System.out.print("Would you like to order another drink? (Y or N) ");
                orderAnotherLiquid = userInput.next();
            }
            
            
            System.out.println(receipt);
            System.out.println("Your total is $" + total);
            receipt = "";
            total = 0;
            
            
            System.out.println();
            System.out.print("Would you like to place another order with us?\n" + 
                        "please enter Y for yes " + "or N for no>>");
            startOrder = userInput.next();
            System.out.println();
        }

        System.out.println();
        System.out.println("Thanks for choosing us!");  
    }
    
    public static void liquidMenu(Scanner userInput) 
    {
        System.out.println("Please choose from the following selections.");
        System.out.println("1. Coffee- $" + COFFEE);
        System.out.println("2. Tea- $" + TEA);
        System.out.println("3. Espresso- $" + ESPRESSO);
        int liquidSelection = userInput.nextInt();
        if (liquidSelection == 1) 
            {
                total = total + COFFEE;
                receipt = receipt + "Coffee @ $" + COFFEE + "\n";
                System.out.println();
                coffeeMenu(userInput);
            } 
            else 
               if (liquidSelection == 2) 
               {
                  total = total + TEA;  
                  receipt = receipt + "Tea @ $" + TEA + "\n";
               } 
            else 
               if (liquidSelection == 3) 
               {
                total = total + ESPRESSO; 
                receipt = receipt + "Espresso @ $" + ESPRESSO + "\n";
                System.out.println();
                expressoMenu(userInput);
               }
    }
    
    public static void expressoMenu(Scanner userInput) 
    {
        System.out.println("Please choose from the following selections.");
        System.out.println("1. Caramel- no charge");
        System.out.println("2. Chocolate- no charge");
        System.out.println("3. One shot- no charge");
        System.out.println("4. Two shots- $" + SHOT_TWO);
        int expressoSelection = userInput.nextInt();
        if (expressoSelection == 1)
                    receipt = receipt + "\t-Caramel (no charge)\n";  
                else if (expressoSelection == 2)
                    receipt = receipt + "\t-Chocolate (no charge)\n";  
                else if (expressoSelection == 3)
                    receipt = receipt + "\t-One shot (no charge)\n";  
                else if (expressoSelection == 4) 
                   {
                    total = total + SHOT_TWO;
                    receipt = receipt + "\t-Two shots ($" + SHOT_TWO + ")\n";
                   }
                
        System.out.println();
        System.out.print("Do you want to add another to your espresso? (Y or N) ");
        String anotherEspressoOption = userInput.next();
        System.out.println();
        if (anotherEspressoOption.equals("Y") || anotherEspressoOption.equals("y"))
            expressoMenu(userInput);
    }
    
    public static void coffeeMenu(Scanner userInput) 
    {
        System.out.println("Please choose from the following selections.");
        System.out.println("1. Iced- no charge");
        System.out.println("2. Cream- $" + CREAM);
        System.out.println("3. Sugar $" + SUGAR);
        int otherSelection = userInput.nextInt();
        if (otherSelection == 1)
                receipt = receipt + "\t-Iced (no charge)\n";
            else if (otherSelection == 2) 
            {
                total = total + CREAM;         
                receipt = receipt + "\t-Cream ($" + CREAM + ")\n";
            } else if (otherSelection == 3) 
            {
                total = total + SUGAR;
                receipt = receipt + "\t-Sugar ($" + SUGAR + ")\n";
            }
        
        System.out.println();
        System.out.print("Do you want to add another to your coffee? (Y or N) ");
        String anotherCoffeeOption = userInput.next();
        System.out.println();
        if (anotherCoffeeOption.equals("Y") || anotherCoffeeOption.equals("y"))
            coffeeMenu(userInput);
    }
}

