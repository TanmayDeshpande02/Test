```java
public void testAscendingSorting() {
        // Open the webpage
        driver.get(baseUrl);

        // Get the text of the first two elements
        WebElement firstElement = driver.findElement(By.xpath("//your_xpath_expression_for_first_element"));
        WebElement secondElement = driver.findElement(By.xpath("//your_xpath_expression_for_second_element"));

        // Get the text of the elements
        String firstText = firstElement.getText();
        String secondText = secondElement.getText();

        // Convert the text to ASCII values
        int firstAsciiValue = convertToAscii(firstText);
        int secondAsciiValue = convertToAscii(secondText);

        // Check if the ASCII values of the first two elements are in ascending order
        assertTrue("First two elements are not sorted in ascending order", firstAsciiValue <= secondAsciiValue);
    }


      @Test
    public void testStringValidation() {
        Pattern pattern = Pattern.compile("^[a-zA-Z\\s\\.,!?'\"]+$");

```

        // Test cases:
        assertTrue(pattern.matcher("This is a valid string.").matches());
        assertFalse(pattern.matcher("1234").matches());  // Contains numbers
        assertFalse(pattern.matcher("hello@example.com").matches());  // Contains email address
    }
```

import java.util.regex.Pattern;
import java.util.regex.Matcher;

// ...

String output = "(9) Records Found";
Pattern pattern = Pattern.compile("\\(([^()]*)\\d[^()]*\\)");
Matcher matcher = pattern.matcher(output);

if (matcher.find()) {
    System.out.println("Digit found within parentheses: " + matcher.group(1));  // Output: "9"
} else {
    System.out.println("No digit found within parentheses.");
}
```
