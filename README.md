# Registration-Form
Registration form using java swing 

It contains different heading, textFields, checkBoxes, ComboBoxes, RdioButtons, Buttons, etc.
First we made a paper layout of how our form will look and then accordingly, we wrote the code 
We first prepared the gui by giving headings and setting there bounds and locations on the window and then added them to the panels
after that we also decided what to print when the user pressed the submit button and accordingly we wrote the ActionPerformed method 
If the entries are written correctly then it will printb all the entries on the screen otherwise will print about what is wrong

//CODE

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class window extends JFrame implements ActionListener{
    private JLabel name , mobile , dob , gender , add , msg , form;
    private Font font = new Font("" , Font.BOLD , 16);
    private JButton sub;
    private JRadioButton m , f;
    private JCheckBox ter;
    private JTextField nam , mo;
    private JTextArea ta , screen;
    private JComboBox date, month, year;
    window()
    {
        super.setTitle("Registration Form");
        super.setLocationRelativeTo(null);
        super.setSize(700 , 500);
        super.setDefaultCloseOperation(EXIT_ON_CLOSE);
        createGui();
        super.setVisible(true);
    }

    public void createGui()
    {
        Container c = getContentPane();
        c.setLayout(null);

        form = new JLabel("Form");
        Font f2 = new Font("" , Font.CENTER_BASELINE , 20);
        form.setFont(f2);
        form.setBounds(260 , 5 , 100 , 40);
        c.add(form);

        c.setBackground(Color.GRAY);

        name = new JLabel("Name");
        name.setFont(font);
        name.setBounds(20 , 50 , 100 ,20);
        c.add(name);

        nam = new JTextField();
        nam.setBounds(130 , 50 , 100 , 20);
        c.add(nam);

        mobile = new JLabel("Mobile");
        mobile.setFont(font);
        mobile.setBounds(20 , 100 , 100 ,20);
        c.add(mobile);

        mo = new JTextField();
        mo.setBounds(130 , 100 , 100 , 20);
        c.add(mo);

        gender = new JLabel("Gender");
        gender.setFont(font);
        gender.setBounds(20 , 150 , 100 , 20);
        c.add(gender);

        m = new JRadioButton("Male");
        f = new JRadioButton("Female");
        m.setSelected(true);     //so that male appears selected by default

        m.setBounds(130 , 150 , 80 , 20);
        f.setBounds(220 , 150 , 80 , 20);

        c.add(m);
        c.add(f);

        //button group so that only one of the buttons is selected at a time
        ButtonGroup b = new ButtonGroup();
        b.add(m);
        b.add(f);

        dob = new JLabel("DOB");
        dob.setBounds(20 , 200 , 100 , 20);
        dob.setFont(font);
        c.add(dob);

        String [] days = {"1" , "2" , "3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20",
        "21","22","23","24","25","26","27","28","29","30"};
        String months[] = {"Jan", "Feb", "March", "april" , "june", "july", "august", "sept", "oct", "nov","Dec"};
        String years[] = {"1995","1996","1997","1998","1999","2000","2001","2002","2003","2004","2005"};

        date = new JComboBox(days);
        month = new JComboBox(months);
        year = new JComboBox(years);

        date.setBounds(130 , 200 , 50 , 20);
        month.setBounds(190 , 200 , 50 , 20);
        year.setBounds(250 , 200 , 60 , 20);

        c.add(date);
        c.add(month);
        c.add(year);

        add = new JLabel("Address");
        add.setFont(font);
        add.setBounds(20 , 250 , 100 , 20);
        c.add(add);

        ta = new JTextArea();
        ta.setBounds(130 , 240 ,200 ,50);
        c.add(ta);

        ter = new JCheckBox("Please accept the terms and conditions");
        ter.setBounds(100 , 300 , 250 ,20);
        c.add(ter);

        sub = new JButton("Submit");
        sub.setBounds(150 , 350 , 80 , 18);
        c.add(sub);

        sub.addActionListener(this);

        screen = new JTextArea();
        screen.setBounds(360 , 50 , 300 , 300);
        c.add(screen);

        msg = new JLabel("");
        Font font1 = new Font("" , Font.ITALIC , 14);
        msg.setFont(font1);
        msg.setBounds(20 , 400 , 300 , 20);
        c.add(msg);
    }

    //this function is for actions i.e if submitted to print msg and if not selected the checbox and etc...
    public void actionPerformed(ActionEvent e)
    {
        if(ter.isSelected())
        {
            msg.setText("Registration done");


            //to print the entered data on the screen
            String n = nam.getText();
            String m = mo.getText();
            String gen = "Male";
            if(f.isSelected())
            {
                gen = "Female";
            }
            String dob1 = date.getSelectedItem() + "/" + month.getSelectedItem() + "/" + year.getSelectedItem();
            String ad = ta.getText();

            screen.setText("Name: " + n + "\n" + "Mobile: " + m + "\n" + "Gender: " + gen + "\n" + "DOB: " + dob1 + "\n" +
                    "Address: " + ad);
        }
        else if(!ter.isSelected())
        {
            msg.setText("Please check the checkBox or check for errors");
            screen.setText("");
        }
    }
}

