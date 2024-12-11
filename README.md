# Manual-test-Case and mini automation testing project TextNG frame work

SWAG LAB WEBSITE 
A manual test case is a set of conditions or steps that are used to verify that a software application works as expected. It is executed manually
##DEMO
![Screenshot 2024-12-08 192417](https://github.com/user-attachments/assets/c7e7c71f-45d4-4719-94b7-b565e9058891)
# automation testing project TextNG frame work

{package maven;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;
}

public class Automation_testing {

    public WebDriver driver;
    String baseUrl = "https://www.saucedemo.com/";
    String driverPath = "C:\\Users\\M S I\\OneDrive\\selenium works\\b\\chromedriver-win64\\chromedriver.exe";

    @BeforeTest
    public void setup() {
        System.setProperty("webdriver.chrome.driver", driverPath);
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get(baseUrl);
    }

    @Test
    public void loginTest() throws InterruptedException {
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();

        String expectedTitle = "Swag Labs";
        String actualTitle = driver.getTitle();
        Assert.assertEquals(actualTitle, expectedTitle, "Login failed: Page title does not match");

        boolean isInventoryVisible = driver.findElement(By.className("inventory_list")).isDisplayed();
        Assert.assertTrue(isInventoryVisible, "Login failed: Inventory page not visible");
    }

    @AfterTest
    public void tearDown() {
        driver.quit();
    }
}
