# New-coding
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class TableDataAutomation {
    public static void main(String[] args) {
        // Set the path to the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver.exe");
        
        // Initialize the WebDriver
        WebDriver driver = new ChromeDriver();
        
        // Navigate to the URL
        driver.get("https://testpages.herokuapp.com/styled/tag/dynamic-table.html");
        
        // Click on the "Table Data" button
        driver.findElement(By.id("populate-table")).click();
        
        // Find the input text box and insert the JSON data
        WebElement textBox = driver.findElement(By.id("data"));
        String jsonData = "[{\"name\" : \"Bob\", \"age\" : 20, \"gender\": \"male\"}, " +
                         "{\"name\": \"George\", \"age\" : 42, \"gender\": \"male\"}, " +
                         "{\"name\": \"Sara\", \"age\" : 42, \"gender\": \"female\"}, " +
                         "{\"name\": \"Conor\", \"age\" : 40, \"gender\": \"male\"}, " +
                         "{\"name\": \"Jennifer\", \"age\" : 42, \"gender\": \"female\"}]";
        textBox.sendKeys(jsonData);
        
        // Click on the "Refresh Table" button
        driver.findElement(By.id("refresh")).click();
        
        // Wait for the table data to be populated
        // You can use explicit waits here
        
        // Retrieve the data from the UI table
        WebElement table = driver.findElement(By.id("table"));
        String tableData = table.getText();
        
        // Compare the UI table data with the expected data
        String expectedData = "Name Age Gender\n" + jsonData; // Adjust the format as needed
        if (tableData.equals(expectedData)) {
            System.out.println("Data matches!");
        } else {
            System.out.println("Data does not match.");
        }
        
        // Close the WebDriver
        driver.quit();
    }
}
