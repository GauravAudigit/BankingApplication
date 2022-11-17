import java.util.Scanner;

public class BankingApplication {

     public static void main(String[] args) {
        Scanner ip = new Scanner(System.in);
         
        System.out.println("To create a new account please enter the required details\n");
        System.out.print("Unique Code:");
        String cid = ip.next();
        System.out.print("\nYour Name:");
        String cname = ip.next();
        System.out.println("\n");
        BankAccount obj = new BankAccount(cname, cid);
        obj.showMenu();   
    }
}
class BankAccount{
    int balance;
    int previousTransation;
    String customerName;
    String customerID;

    BankAccount(String cname , String cid){
        customerName = cname;
        customerID = cid;
    }

    void deposit(int amount){
        if(amount > 0){
            balance = balance + amount;
            previousTransation = amount;
        }
    }

    void withdraw(int amount){
        if(amount > 0){
            balance = balance - amount;
            previousTransation = -amount;
        }
    }

    void getprevioustransaction() {
        if(previousTransation > 0) {
            System.out.println("Deposited: " + previousTransation);
        }
        else if(previousTransation < 0) {
            System.out.println("Withdraw: " +Math.abs(previousTransation));
        }
        else {
            System.out.println("No Transaction Occured");
        }
    }

    void showMenu(){

        char option = '\0';
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Welcome " +customerName);
        System.out.println("Your ID " +customerID);
        System.out.println("\n");

        System.out.println("A : Check Your Balance");
        System.out.println("B : Deposit");
        System.out.println("C : Withdraw");
        System.out.println("D : Previous Transaction");
        System.out.println("E : Exit The System");

        do {
            System.out.println("==============================================");
            System.out.println("Enter Your Option");
            System.out.println("==============================================");
            option = scanner.next().charAt(0);
            System.out.println("\n");

            switch (option) {

                case 'A':
                   System.out.println("--------------------------------------------------------");
                   System.out.println("Balance = "+balance);
                   System.out.println("--------------------------------------------------------");
                   System.out.println("\n");
                   break;
                
                case 'B':
                   System.out.println("--------------------------------------------------------");
                   System.out.println("Enter An Amount To Deposit ");
                   System.out.println("--------------------------------------------------------");

                   int amount = scanner.nextInt();
                   deposit(amount);
                   System.out.println("\n");
                   break; 
                
                case 'C':
                   System.out.println("-------------------------------------------");
                   System.out.println("Enter An Amount To Withdraw ");
                   System.out.println("-------------------------------------------");

                   int amount2 = scanner.nextInt();
                   withdraw(amount2);
                   System.out.println("\n");
                   break; 
                   
                case 'D':
                   System.out.println("--------------------------------------------------------");
                   getprevioustransaction();
                   System.out.println("--------------------------------------------------------");
                   System.out.println("\n");
                   break;  
                   
                case 'E':
                    System.out.println("=====================================================================================");
                    break;    

                   default:
                        System.out.println("Invalid Option!! Please Enter Correct Option...");
                     break;
            }
        }
        while(option !='E');
             System.out.println("Thank You For Using Our Services......!!");
    }

}