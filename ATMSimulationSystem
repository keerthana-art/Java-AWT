import java.awt.*;
import java.awt.event.*;

public class ATMSimulation extends Frame {
    private TextField accountField, amountField, pinField;
    private TextArea displayArea;
    private Button withdrawButton, depositButton, balanceButton, exitButton;
    private double balance = 1000.00; // Initial balance
    private int accountNumber = 12345;
    private int pin = 1234;
    private boolean isLoggedIn = false;

    public ATMSimulation() {
        setTitle("ATM Simulation");
        setSize(400, 500);
        setLayout(new FlowLayout());
        setBackground(Color.LIGHT_GRAY);

        // Initialize components
        Label accountLabel = new Label("Account Number: ");
        accountField = new TextField(20);
        Label pinLabel = new Label("PIN: ");
        pinField = new TextField(20);
        pinField.setEchoChar('*');
        
        Label amountLabel = new Label("Amount: ");
        amountField = new TextField(20);
        
        displayArea = new TextArea(10, 40);
        displayArea.setEditable(false);

        Button loginButton = new Button("Login");
        withdrawButton = new Button("Withdraw");
        depositButton = new Button("Deposit");
        balanceButton = new Button("Check Balance");
        exitButton = new Button("Exit");

        // Initially disable transaction buttons
        withdrawButton.setEnabled(false);
        depositButton.setEnabled(false);
        balanceButton.setEnabled(false);

        // Add components
        add(accountLabel);
        add(accountField);
        add(pinLabel);
        add(pinField);
        add(loginButton);
        add(amountLabel);
        add(amountField);
        add(withdrawButton);
        add(depositButton);
        add(balanceButton);
        add(exitButton);
        add(displayArea);

        // Login button action
        loginButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                validateLogin();
            }
        });

        // Withdraw button action
        withdrawButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                withdraw();
            }
        });

        // Deposit button action
        depositButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                deposit();
            }
        });

        // Balance button action
        balanceButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                checkBalance();
            }
        });

        // Exit button action
        exitButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.exit(0);
            }
        });

        // Window closing event
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });
    }

    private void validateLogin() {
        try {
            int inputAccount = Integer.parseInt(accountField.getText());
            int inputPin = Integer.parseInt(pinField.getText());

            if (inputAccount == accountNumber && inputPin == pin) {
                isLoggedIn = true;
                withdrawButton.setEnabled(true);
                depositButton.setEnabled(true);
                balanceButton.setEnabled(true);
                displayArea.setText("Login successful!\nWelcome to ATM System");
            } else {
                displayArea.setText("Invalid account number or PIN!");
            }
        } catch (NumberFormatException e) {
            displayArea.setText("Please enter valid numbers!");
        }
    }

    private void withdraw() {
        if (!isLoggedIn) {
            displayArea.setText("Please login first!");
            return;
        }

        try {
            double amount = Double.parseDouble(amountField.getText());
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                displayArea.setText(String.format("Withdrawal successful!\nAmount: $%.2f\nNew Balance: $%.2f", 
                    amount, balance));
            } else {
                displayArea.setText("Invalid amount or insufficient funds!");
            }
        } catch (NumberFormatException e) {
            displayArea.setText("Please enter a valid amount!");
        }
        amountField.setText("");
    }

    private void deposit() {
        if (!isLoggedIn) {
            displayArea.setText("Please login first!");
            return;
        }

        try {
            double amount = Double.parseDouble(amountField.getText());
            if (amount > 0) {
                balance += amount;
                displayArea.setText(String.format("Deposit successful!\nAmount: $%.2f\nNew Balance: $%.2f", 
                    amount, balance));
            } else {
                displayArea.setText("Please enter a positive amount!");
            }
        } catch (NumberFormatException e) {
            displayArea.setText("Please enter a valid amount!");
        }
        amountField.setText("");
    }

    private void checkBalance() {
        if (!isLoggedIn) {
            displayArea.setText("Please login first!");
            return;
        }
        displayArea.setText(String.format("Current Balance: $%.2f", balance));
    }

    public static void main(String[] args) {
        ATMSimulation atm = new ATMSimulation();
        atm.setVisible(true);
    }
}
