# Calculator---GUI

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.Font;
import java.awt.GridLayout;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

/**
 *
 * @author aamna
 */
public class GUI {
 
    JFrame fr;
    JButton[] btnArr;
    JTextField tfMain,tfSub;
    JPanel panBtn,panTf;
    BtnHandler hnd;
    
    public GUI() {
        initGUI();
    }
    public void initGUI()
    {
        //Array to store text on buttons
        String[] btnText = {"^","^2","del","C","MC","M+","M-","/","7","8","9","*","4","5","6","-","1","2","3","+","1/x","0",".","="};
        
        //making frame
        fr = new JFrame("Calculator");
        fr.setLayout(new BorderLayout());
        
        // making panel for buttons
        panBtn = new JPanel();
        //setting panel's size
        panBtn.setPreferredSize(new Dimension(950,350));
        //setting layout of panel to grid layout which contains 6-rows and 4-columns
        panBtn.setLayout(new GridLayout(6,4));
        
        //initializing - btnhandler - which contains working fumctionalities of buttons on calculator
        hnd = new BtnHandler(this);
        
        //making a panel for text fields
        //tfMain - shows the equation
        //subMain - shows the answer resulting in equation from tfMain
        panTf = new JPanel();
        panTf.setPreferredSize(new Dimension(100,100));
        panTf.setLayout(new GridLayout(2,2));
        
        //making tfMain - of size 20 
        tfMain = new JTextField(20);
        tfMain.setBorder(null);
        tfMain.setEditable(false);
        tfMain.setFont(new Font("Verdena",Font.BOLD,20));
        tfMain.setBackground(Color.WHITE);
        
        //makinh subMain - of size 20
        tfSub = new JTextField(20);
        tfSub.setBorder(null);
        tfSub.setEditable(false);
        tfSub.setFont(new Font("Verdena",Font.BOLD,20));
        tfSub.setBackground(Color.WHITE);
        
        //adding both the text fields in textfield panel(panTf)
        panTf.add(tfMain);
        panTf.add(tfSub);
        
        //total number of buttons on calculator - 24
        int btnCount=24;
        //initializing Button Array
        btnArr = new JButton[btnCount];
        
        //initializing each button, setting it's font-size, text, color
        for (int i = 0; i < btnCount; i++) {
            btnArr[i] = new JButton();
           //btnArr[i].setText(Integer.toString(i));
           btnArr[i].setText(btnText[i]);
           btnArr[i].setFont(new Font("Verdena",Font.BOLD,20));
           // setActionCommand and addActionListener - for it contains working in btnHandler 
           btnArr[i].setActionCommand(btnText[i]);
           btnArr[i].addActionListener(hnd);
           //set background of buttons 
           if(btnArr[i].getText()=="MC"||btnArr[i].getText()=="M+"||btnArr[i].getText()=="M-"||btnArr[i].getText()=="MR")
           {
                btnArr[i].setBackground(Color.ORANGE);
           }
           else if(btnArr[i].getText()=="=")
           {
                btnArr[i].setBackground(Color.GREEN);
           }
           else if(btnArr[i].getText()=="del"||btnArr[i].getText()=="C")
           {
                btnArr[i].setBackground(Color.YELLOW);
           }
           else if(btnArr[i].getText()=="^2"||btnArr[i].getText()=="^"||btnArr[i].getText()=="/"||btnArr[i].getText()=="*"||btnArr[i].getText()=="-"||btnArr[i].getText()=="+")
           {
                btnArr[i].setBackground(Color.LIGHT_GRAY);
           }
           else
           {
               btnArr[i].setBackground(Color.WHITE);
           }
           btnArr[i].setPreferredSize(new Dimension(10,10));
           panBtn.add(btnArr[i]);
        }
        //setting tfMain allignment to right while subMain has it's to left
        tfMain.setHorizontalAlignment(JTextField.RIGHT);
        
        //adding in frame - textfield panel and button panel
        fr.add(panTf,BorderLayout.NORTH);
        fr.add(panBtn,BorderLayout.CENTER);
        
       //setting size of frame
        fr.setSize(500,500);
      //setting location of frame on screen
        fr.setLocation(200,200);
        fr.setLocationRelativeTo(null);
        //calculator's frame cannot be resized - it is of fixed size
        fr.setResizable(false);
        fr.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        //fr.pack();
        fr.setVisible(true); 
    }
}
   
