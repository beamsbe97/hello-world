// Full Name: Nguyen Quoc An
// Part time
// Tutorial Group
// Declaration: 
//this is my own lab and I have not passed my lab to anyone in this class

import java.util.Scanner;
enum UOWGrade {HD, D, C, P, F}
class AnNguyen_A1
{
    
    
    public static void main (String [] args)
    {
        Scanner input = new Scanner(System.in);
        String item1;
        String item2;
        String item3;
        double price1;
        double price2;
        double price3;
        int qty1;
        int qty2;
        int qty3;

        System.out.printf("Welcome to An Nguyen online service%n");
        System.out.printf("-------------------------------%n");
        System.out.printf("Enter 3 items to be sold%n");

        //Prompt use to enter the item names
        System.out.print("1.");
        item1 = input.nextLine();

        System.out.print("2.");
        item2 = input.nextLine();
        
        System.out.print("3.");
        item3 = input.nextLine();

        //Prompt user to input qty and price of the items
        System.out.printf("Enter the quantity and price of %s:", item1);
        qty1 = input.nextInt();
        price1 = input.nextDouble();

        System.out.printf("Enter the quantity and price of %s:", item2);
        qty2 = input.nextInt(); 
        price2 = input.nextDouble();
        
        System.out.printf("Enter the quantity and price of %s:", item3);
        qty3 = input.nextInt();
        price3 = input.nextDouble();

        //Display summary of the items
        System.out.printf("%n");
        System.out.printf("Summary of the items:%n");
        System.out.printf("-------------------------------------------------------------%n");
        System.out.printf("Items\t\t\t\tQuantity\t    Price%n");
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item1, qty1, price1);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item2, qty2, price2);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item3, qty3, price3);

        //Swap 1st and 2nd items
        String temp_item = item1;
        int temp_qty = qty1;
        double temp_price = price1;

        item1 = item2;
        qty1 = qty2;
        price1 = price2;

        item2 = temp_item;
        qty2 = temp_qty;
        price2 = temp_price;

        //Display summary after the swap
        System.out.printf("%n");
        System.out.printf("Summary of items after the swap%n");
        System.out.printf("-------------------------------------------------------------%n");
        System.out.printf("Items\t\t\t\tQuantity\t       Price%n");
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item1, qty1, price1);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item2, qty2, price2);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item3, qty3, price3);

        //Customer's orders
        System.out.printf("%n");
        System.out.printf("Please place your order%n");
        System.out.printf("-------------------------------%n");
        System.out.printf("Number of %s:", item1);
        int orderQty1 = input.nextInt();
        System.out.printf("Number of %s:", item2); 
        int orderQty2 = input.nextInt();   
        System.out.printf("Number of %s:", item3);
        int orderQty3 = input.nextInt();   
        
        //calculate cost of orders
        double cost1 = findItemCost(orderQty1, price1);
        double cost2 = findItemCost(orderQty2, price2);
        double cost3 = findItemCost(orderQty3, price3);
        double subtotal = cost1 + cost2 + cost3;
        double gst = (subtotal/100) * 7;
        double totalCost = subtotal + gst;

        //display summary of order
        System.out.printf("%n");
        System.out.printf("Summary of your order%n");
        System.out.printf("-------------------------------%n");
        System.out.printf("%n");
        System.out.printf("Items\t\t\t\tQuantity\t     Cost%n");
        System.out.printf("-------------------------------------------------------------%n");
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item1, orderQty1, cost1);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item2, orderQty2, cost2);
        System.out.printf("%-22s\t\t%-5d\t\t%10.2f%n", item3, orderQty3, cost3);
        System.out.printf("-------------------------------------------------------------%n");
        System.out.printf("Subtotal  \t\t\t\t\t%10.2f%n", subtotal);
        System.out.printf("GST       \t\t\t\t\t%10.2f%n", gst);
        System.out.printf("Total cost\t\t\t\t\t%10.2f%n", totalCost);

        //Delivery information
        System.out.printf("Delivery information%n");
        System.out.printf("Customer name:%n");
        input.nextLine();
        System.out.printf("Collection point:%n");
        input.nextLine();
        System.out.printf("Note that payment by cash upon delivery%n");
        System.out.printf("Thank you for using our system%n");

        //Balance report
        int stockbal_1 = findStockBalance(qty1, orderQty1);
        int stockbal_2 = findStockBalance(qty2, orderQty2);
        int stockbal_3 = findStockBalance(qty3, orderQty3);

        //Display stock balance report
        System.out.printf("Balance report%n");
        System.out.printf("-------------------------------------------------------------%n");
        System.out.printf("%n");
        System.out.printf("Item\t\t\t  Quantity  \tSold\tBalance%n");
        System.out.printf("%-22s\t\t%-5d\t\t%-5d\t%-5d%n", item1, qty1, orderQty1, stockbal_1);
        System.out.printf("%-22s\t\t%-5d\t\t%-5d\t%-5d%n", item2, qty2, orderQty2, stockbal_2);
        System.out.printf("%-22s\t\t%-5d\t\t%-5d\t%-5d%n", item3, qty3, orderQty3, stockbal_3);

    }

    public static double findItemCost( int qty, double price)
    {  
        return qty * price;    
    }

    public static int findStockBalance(int qty, int orderQty)
    {
        return qty - orderQty;
    }
}
