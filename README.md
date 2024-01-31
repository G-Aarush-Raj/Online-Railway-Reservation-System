//Online Railway Reservation System

    
    
    import javax.swing.*;
    import java.awt.event.*;

    public class OnlineReservationSystem extends JFrame {
    private JTextField usernameField;
    private JPasswordField passwordField;
    private JTextField trainNameField;
    private JTextField seatNumberField;
    private JTextField passengersField;
    public OnlineReservationSystem() {
        setTitle("Online Reservation System");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JTabbedPane tabbedPane = new JTabbedPane();
        JPanel loginPanel = new JPanel();
        usernameField = new JTextField(20);
        passwordField = new JPasswordField(20);
        JButton loginButton = new JButton("Login");

        loginButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String username = usernameField.getText();
                String password = new String(passwordField.getPassword());
                if (username.equals("user") && password.equals("password")) {
                    tabbedPane.setEnabledAt(1, true);  // Enable Reservation Form tab
                    tabbedPane.setEnabledAt(2, true);  // Enable Cancellation Form tab
                } else {
                    JOptionPane.showMessageDialog(OnlineReservationSystem.this, "Invalid login credentials");
                }
            }
        });

        loginPanel.add(new JLabel("Username:"));
        loginPanel.add(usernameField);
        loginPanel.add(new JLabel("Password:"));
        loginPanel.add(passwordField);
        loginPanel.add(loginButton);

        JPanel reservationPanel = new JPanel();
        trainNameField = new JTextField(20);
        seatNumberField = new JTextField(20);
        JButton reserveButton = new JButton("Reserve");

        reserveButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String trainName = trainNameField.getText();
                String seatNumber = seatNumberField.getText();
                JOptionPane.showMessageDialog(OnlineReservationSystem.this, "Reservation Successful!");
            }
        });

        reservationPanel.add(new JLabel("Train Name:"));
        reservationPanel.add(trainNameField);
        reservationPanel.add(new JLabel("Seat Number:"));
        reservationPanel.add(seatNumberField);
        reservationPanel.add(reserveButton);

        JPanel cancellationPanel = new JPanel();
        passengersField = new JTextField(20);
        JButton cancelButton = new JButton("Cancel");

        cancelButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String passengers = passengersField.getText();
                JOptionPane.showMessageDialog(OnlineReservationSystem.this, passengers + " tickets canceled successfully!");
            }
        });

        cancellationPanel.add(new JLabel("Number of Passengers:"));
        cancellationPanel.add(passengersField);
        cancellationPanel.add(cancelButton);

        tabbedPane.addTab("Login", loginPanel);
        tabbedPane.addTab("Reservation", reservationPanel);
        tabbedPane.addTab("Cancellation", cancellationPanel);
        tabbedPane.setEnabledAt(1, false);
        tabbedPane.setEnabledAt(2, false);

        add(tabbedPane);
        setVisible(true);
    }

    public static void main(String[] args) {
        new OnlineReservationSystem();
    }
}
