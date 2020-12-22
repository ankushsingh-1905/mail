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

    
    

    String ID="onet66793";
    String PW="Test@12345678";
    String TO="akyy.19@gmail.com";
    String SUBJECT="Testing Suite for QA";
    String BODY="This is my sample code with attachment";
  
    WD.findElement(By.id("identifierId")).sendKeys(ID);

    WD.findElement(By.className("VfPpkd-RLmnJb")).click();

    Thread.sleep(2000);

    WD.findElement(By.name("password")).sendKeys(PW);

    WD.findElement(By.className("VfPpkd-RLmnJb")).click();

    
    Thread.sleep(3000);
    WD.findElement(By.xpath("//div[contains(text(),'Compose')]")).click();
    // To send
    Thread.sleep(3000);
    WD.findElement(By.name("to")).sendKeys(TO);
    WD.findElement(By.name("subjectbox")).sendKeys(SUBJECT);
    WD.findElement(By.cssSelector(".Am.Al.editable.LW-avf")).sendKeys(BODY);
    Thread.sleep(3000);
    
    WD.findElement(By.xpath("//*[@class='a1 aaA aMZ']")).click();
    
    
    
  
    Robot robo = new Robot();

    StringSelection att = new StringSelection("C:\\Users\\A19GE5QX\\Desktop\\1");
    Toolkit.getDefaultToolkit().getSystemClipboard().setContents(att, null);

    robo.keyPress(KeyEvent.VK_CONTROL);
    robo.keyPress(KeyEvent.VK_V);

    robo.keyRelease(KeyEvent.VK_CONTROL);
    robo.keyRelease(KeyEvent.VK_V);

    Thread.sleep(2000);
    robo.keyPress(KeyEvent.VK_ENTER);
    robo.keyRelease(KeyEvent.VK_ENTER);
    
    Thread.sleep(2000);
    WD.findElement(By.xpath("//div[text()='Send']")).click();


  }

}
