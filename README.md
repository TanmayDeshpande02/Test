# PAGEBINS :

package pageBins;
 
import static org.junit.jupiter.api.Assertions.*;
 
import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Disabled;
import org.junit.jupiter.api.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.edge.EdgeDriver;
 
import Orangehrm_class.TestRec;
 
 
class Personal_Details_Test {
	static WebDriver driver ;
	static PersonalDetails p1;

	@BeforeAll
	static void openBrowser() throws Exception {
		Thread.sleep(2000);
		System.setProperty("webdriver.edge.driver","Drivers/msedgedriver.exe");
		driver = new EdgeDriver();
		driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");	
		p1=new TestRec(driver);
		//Login
		Thread.sleep(2000);
		p1.setUn("Admin");
		Thread.sleep(2000);
		p1.setPwd("admin123");
		Thread.sleep(2000);
		p1.setBtn();
		Thread.sleep(2000);
		//assertTrue(driver.getCurrentUrl().contains("dashboard"));
	}

	@Test
	public void SearchDetails() throws InterruptedException
	{
		Thread.sleep(2000);
		driver.navigate().to("https://opensource-demo.orangehrmlive.com/web/index.php/recruitment/viewCandidates");
		Thread.sleep(3000);
        p1.searchBtn();
		assertEquals("Records Found", driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[2]/div[2]/div/span")).getText());
	}

	@Test
	public void keyword_search() throws InterruptedException
	{
		Thread.sleep(2000);
        p1.setkeyword("java");
		Thread.sleep(2000);
		p1.searchBtn();
		Thread.sleep(2000);
		assertEquals("Records Found", driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[2]/div[2]/div/span")).getText());
	}

    @Test
	public void name_search() throws InterruptedException
	{
		Thread.sleep(2000);
		// driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/div[2]/div/div/input")).sendKeys("John");
		cn.setcandidateName("Jhon");
        Thread.sleep(2000);
		p1.searchBtn();
		Thread.sleep(2000);
		assertEquals("Records Found", driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/span")).getText());
	}

   @Test
	public void name_search_lower() throws InterruptedException
	{
		Thread.sleep(2000);
		// driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/div[2]/div/div/input")).sendKeys("John");
		cn.setcandidateName("jhon");
        Thread.sleep(2000);
		p1.searchBtn();
		Thread.sleep(2000);
		assertEquals("Records Found", driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/span")).getText());
	}

    // assertEquals("Records Found", driver.findElement(By.xpath("//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/span")).getText());
    // assertEquals("Records Found", driver.findElement(By.xpath("//*[@id=\"app\"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/span")).getText());

    @Test
    public void add() throws InterruptedException
    {
        p1.addBtn();
        Thread.sleep(2000);
        p1.setfname("Tanmay");
        p1.setlname("D");
        p1.setemail("abc@gmail.com");
        p1.savebtn();
       assertEquals("Error", adriver.switchTo().alert().getText());

    }


    @Test
    public void Actions_view() throws InterruptedException
    {
        p1.clickaction();
        String currentUrl = driver.getCurrentUrl();
        assertNotEquals("https://opensource-demo.orangehrmlive.com/web/index.php/recruitment/viewCandidates", currentUrl);
    }

    public void Actions_view() throws InterruptedException
    {
        p1.delete_action();
        assertEquals("The selected record will be permanently deleted. Are you sure you want to continue?", driver.switchTo().alert().getText());
    }
 
	@AfterAll
	static void afterAll() throws Exception {
		driver.close();
	}
 
}

# Classes

package Orangehrm_class;
 
import org.junit.jupiter.api.BeforeAll;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.support.CacheLookup;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;
 
 
public class TestRec {
	WebDriver driver;
	//Login
	@FindBy(name = "username")
	@CacheLookup
	WebElement un;
 
	@FindBy(name = "password")
	@CacheLookup
	WebElement pwd;

	@FindBy(xpath = "//*[@id=\"app\"]/div[1]/div/div[1]/div/div[2]/div[2]/form/div[3]/button")
    @CacheLookup
	WebElement btn;

    

    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[4]/button[2]")
    @CacheLookup
    WebElement searchBtn;

     @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[4]/button[2]")
    @CacheLookup
    WebElement addBtn;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[1]/div/div[2]/div/div/input")
    @CacheLookup
    WebElement cn;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[2]/div/div[2]/div/div[2]/input")
    @CacheLookup
    WebElement ky;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div/form/div[1]/div/div/div/div[2]/div[1]/div[2]/input")
    @CacheLookup
    WebElement fname;

    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div/form/div[1]/div/div/div/div[2]/div[3]/div[2]/input")
    @CacheLookup
    WebElement lname;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div/form/div[3]/div/div[1]/div/div[2]/input")
    @CacheLookup
    WebElement email;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div/form/div[8]/button[2]")
    @CacheLookup
    WebElement save;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[1]/header/div[2]/nav/ul/li[2]/a")
    @CacheLookup
    WebElement vacancy;

    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[2]/div[3]/div/div/div[1]/div/div/div[1]/div[2]/div/div/button[1]/i")
    @CacheLookup
    WebElement view_action;


    @FindBy(xpath = "//*[@id="app"]/div[1]/div[2]/div[2]/div/div[2]/div[3]/div/div/div[1]/div/div/div[1]/div[2]/div/div/button[2]/i")
    @CacheLookup
    WebElement delete_action;

	//=======================================================================================

 
	public TestRec(WebDriver driver) {
		this.driver = driver;
		PageFactory.initElements(driver, this);
	}
    
	//====================================Login==============================================
	
    public WebElement getUn() {
		return un;
	}
	public void setUn(String txtun) {
		un.sendKeys(txtun);
	}
	public WebElement getPwd() {
		return pwd;
	}
	public void setPwd(String txtpwd) {
		pwd.sendKeys(txtpwd);
	}
	public void setBtn() {
		btn.click();
	}


    public WebElement getcandidateName() {
		return cn;
	}
 
	public void setcandidateName(String name) {
		cn.sendKeys(name);
	}
 
	public WebElement getkeyword() {
		return ky;
	}
 
	public void setkeyword(String kw) {
		ky.sendKeys(kw);
	}

 
    // add

    public void getfname(String fn){
        return fn;
    }
    public void setfname(String fn){
        fname.sendKeys(fn);
    }

    public void getlname(String ln){
        return ln;
    }
    public void setlname(String ln){
        lname.sendKeys(ln);
    }

    public void getemail(String emal){
        return emal;
    }
    public void setemail(String emal){
        email.sendKeys(emal);
    }

    public void clickvacancy(){
        vacancy.click();
    }

    public void clickaction(){
        view_action.click();
    }

    public void delete_action(){
        delete_action.click();
    }
	
	//===========================Search===============================================
	

    public void searchBtn() {
            searchBtn.click();
    }

    public void savebtn(){
        save.click();
    }
    // -------------- add ----------------

 public void addBtn() {
            addBtn.click();
    }

 
}


