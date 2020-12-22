import java.awt.AWTException;
import java.awt.Robot;
import java.awt.Toolkit;
import java.awt.datatransfer.StringSelection;
import java.awt.event.KeyEvent;
import java.io.IOException;



import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

import org.openqa.selenium.firefox.FirefoxDriver;



public class AddingCartItems {

  public static void main(String[] args) throws InterruptedException, AWTException, IOException {
    // TODO Auto-generated method stub

    System.setProperty("webdriver.gecko.driver",
        "C:\\Users\\A19GE5QX\\Desktop\\Daily Tasks\\Selenium\\driver\\geckodriver.exe");

    WebDriver WD = new FirefoxDriver();

    
    WD.get("https://mail.google.com/");

    WD.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
    //Implicit wait for load somwhere i have used threads because explicit wait wasn't working on google site or maybe due to my internet connection
    

    String ID="onet66793";//CreatedTesting ID without security page
    String PW="Test@12345678";//CreatedTesting PW without security page
    String TO="akyy.19@gmail.com";//You can enter your email also
    String SUBJECT="Testing Suite for QA";//Any Subject according to your need
    String BODY="This is my sample code with attachment";//Any Test body according to your need
   
  
  
   // Login Steps
    WD.findElement(By.id("identifierId")).sendKeys(ID);

    WD.findElement(By.className("VfPpkd-RLmnJb")).click();

    Thread.sleep(2000);

    WD.findElement(By.name("password")).sendKeys(PW);

    WD.findElement(By.className("VfPpkd-RLmnJb")).click();

    //Composing a mail 
    
    Thread.sleep(3000);
    WD.findElement(By.xpath("//div[contains(text(),'Compose')]")).click();
   
   // To write sento,subject and body
    
    Thread.sleep(3000);
    WD.findElement(By.name("to")).sendKeys(TO);
    WD.findElement(By.name("subjectbox")).sendKeys(SUBJECT);
    WD.findElement(By.cssSelector(".Am.Al.editable.LW-avf")).sendKeys(BODY);
    Thread.sleep(3000);
    
    //Attaching xpath click
    
    WD.findElement(By.xpath("//*[@class='a1 aaA aMZ']")).click();
    
    
    
  
    //Robo object to pull data from local computer
    Robot robo = new Robot();

    StringSelection att = new StringSelection("C:\\Users\\A19GE5QX\\Desktop\\1"); //Attachment file, attach your file here see syntax for mac as it is for windows
    
    Toolkit.getDefaultToolkit().getSystemClipboard().setContents(att, null);

    robo.keyPress(KeyEvent.VK_CONTROL);
    robo.keyPress(KeyEvent.VK_V);

    robo.keyRelease(KeyEvent.VK_CONTROL);
    robo.keyRelease(KeyEvent.VK_V);

    Thread.sleep(3000);
    robo.keyPress(KeyEvent.VK_ENTER);
    robo.keyRelease(KeyEvent.VK_ENTER);
    
    //Send Mail
    Thread.sleep(3000);
    WD.findElement(By.xpath("//div[text()='Send']")).click();
    
    //logging Out is optional therfore i didn't make it
    
    //Want to close window then WD.close();



  }

}
