# Fermigame

import java.util.Random;
import java.util.Scanner;


public class GameOfFermi {

  public static void main(String[] args) {
   Game g1 = new Game();
   g1.run();
  }
}

class Game{
  
final private int p1;
final private int p2;
final private int p3;
 private int g1;
 private int g2;
 private int g3;
 private String guess;
 private String hint;
 private Random rn;
 private Scanner sc ;
  public Game()
  {
  rn=new Random();
  sc = new Scanner(System.in);
  guess="";
  hint="";
    p1= rn.nextInt(10);
    p2= rn.nextInt(10);
    p3= rn.nextInt(10);
  }
  public void guess(int g1,int g2,int g3)
  {
    this.g1=g1;
    this.g2=g2;
    this.g3=g3;
    this.guess=g1+" "+g2+" "+g3;
    
  }
  public void getHint()
  {

  this.hint=
  g1Hint()+" "+g2Hint()+" "+g3Hint();
    
  }
  public String explanation ()
  {
    String explain="";
    if(g1Hint().equals("fermi"))
explain+="value "+g1+" matches at the correct position";
   else  if(g1Hint().equals("pico"))
explain+="value "+g1+" matches at the wrong position";
    else
explain+="value "+g1+" doesn't match";

if(g2Hint().equals("fermi"))
explain+="\nvalue "+g2+" matches at the correct position";
   else  if(g2Hint().equals("pico"))
explain+="\nvalue "+g2+" matches at the wrong position";
    else
explain+="\nvalue "+g2+" doesn't match";

if(g3Hint().equals("fermi"))
explain+="\nvalue "+g3+" matches at the correct position\n";
   else  if(g3Hint().equals("pico"))
explain+="\nvalue "+g3+" matches at the wrong position\n";
    else
explain+="\nvalue "+g3+" doesn't match\n";
    return explain;
  }
  
  public String g1Hint() 
  {
    if(p1==g1)
    return "fermi";
    else if(p1!=g1&&p2==g1||p3==g1)
    return "pico";
    else if(p1!=g1&&p2!=g1&&p3!=g1)
    return "nano";
    else
    return "";
  }
  public String g2Hint() 
  {
    if(p2==g2)
    return "fermi";
    else if(p2!=g2&&p1==g2||p3==g2)
    return "pico";
    else if(p1!=g2&&p2!=g2&&p3!=g2)
    return "nano";
    else
    return "";
  }
  public String g3Hint() 
  {
    if(p3==g3)
    return "fermi";
    else if(p3!=g3&&p2==g3||p1==g3)
    return "pico";
    else if(p1!=g3&&p2!=g3&&p3!=g3)
    return "nano";
    else
    return "";
  }
  public void displayDetails()
  {
    System.out.println("Guess\t\thint");
    System.out.println(this.guess+"\t\t"+this.hint);
  System.out.println("\nexplanation");
  System.out.println(explanation());
   
  }
  public void run()
  {
  
int g1,g2,g3;
int attempt=0;
String fermi="fermi fermi fermi";
  
    while(true)
    {  
      System.out.println("guess three different number (0 to 9):");
      g1=sc.nextInt();
      g2=sc.nextInt();
      g3=sc.nextInt();
      guess(g1,g2,g3);
      getHint();
      displayDetails();
      attempt++;
      if(this.hint.equals(fermi))
      {
      System.out.println("you have guessed correct \npositions in "+attempt+" attempts");
      break;
      }
    }
  }
}//end class
