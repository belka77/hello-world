package lession2;

import org.junit.Assert;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;

import java.util.List;

import static org.junit.Assert.*;

public class DelfiTest {
    private static final String TITLE = "Sportisti atvadās no Phjončhanas – ziemas olimpisko spēļu noslēguma ceremonija. Teksta tiešraide";
    private static final String MAIN_PAGE_WEB_URL = "http://www.delfi.lv/";
    private static final String MAIN_PAGE_MOBILE_URL = "http://m.delfi.lv/";
    private static final By ARTICLE_TITLE = By.xpath("//a[@class='top2012-title']");
    private static final By ARTICLE_TITLE_MOBILE = By.xpath("//a[@class='md-scrollpos']");

    @Test
    public void DelfiTest () {
        System.setProperty("webdriver.gecko.driver", "C:/geckodriver.exe");
        WebDriver driver = new FirefoxDriver();
        driver.manage() .window() .maximize();
        driver.get (MAIN_PAGE_WEB_URL);
        List <WebElement> articleTitles = driver.findElements(ARTICLE_TITLE_MOBILE);
        assertTrue( "Title list is empty",articleTitles.size()!=0);
        boolean isTitlePresent = false;
        for (WebElement articleTitle : articleTitles) {
            if (articleTitle.getText().equals(TITLE)) {
                isTitlePresent = true;
                break;
            }
            assertTrue("Article is not found", isTitlePresent);
        }
@Test
   public void DelfiTestMobile () {
            System.setProperty("webdriver.gecko.driver", "C:/geckodriver.exe");
            WebDriver driver = new FirefoxDriver();
            driver.manage() .window() .maximize();
            driver.get (MAIN_PAGE_MOBILE_URL);
            List <WebElement> articleTitles = driver.findElements(ARTICLE_TITLE_MOBILE);
            assertTrue( "Title list is empty",articleTitles.size()!=0);
            boolean isTitlePresent = false;
            for (WebElement articleTitle : articleTitles) {
                if (articleTitle.getText().equals(TITLE)) {
                    isTitlePresent = true;
                    break;
                }
                assertTrue("Article is not found", isTitlePresent);
            }
