
import java.util.Scanner;

class B_a_n_k_Acc {
    private double balance;

    public B_a_n_k_Acc(double initialBalance) 
    {
        balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit of $" + amount + " successful.");
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal of $" + amount + " successful.");
            return true;
        } else {
            System.out.println("Invalid withdrawal amount or insufficient balance.");
            return false;
        }
    }
}

class ATM {
    private B_a_n_k_Acc account;

    public ATM(B_a_n_k_Acc userAccount) {
        this.account = userAccount;
    }

    public void displayOptions() {
        System.out.println("\nATM Menu:");
        System.out.println("1. Check Balance");
        System.out.println("2. Deposit");
        System.out.println("3. Withdraw");
        System.out.println("4. Exit");
    }

    public void run() {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            displayOptions();
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Balance: $" + account.getBalance());
                    break;

                case 2:
                    System.out.print("Enter deposit amount: $");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;

                case 3:
                    System.out.print("Enter withdrawal amount: $");
                    double withdrawalAmount = scanner.nextDouble();
                    account.withdraw(withdrawalAmount);
                    break;

                case 4:
                    System.out.println("Exiting ATM. Thank you!");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}

public class m_a_i_n {
    public static void main(String[] args) {
        double initialBalance = 1000.0; // Initial balance for the bank account
        B_a_n_k_Acc  userAccount = new  B_a_n_k_Acc (initialBalance);
        ATM atm = new ATM(userAccount);
        atm.run();
    }
}

