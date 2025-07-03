public class EntrataTests extends BaseTest {

  HomePage home;

  @BeforeClass
  public void initPage() {
    home = new HomePage(driver);
  }

  @Test(priority = 1)
  public void testHomeTitleContainsEntrata() {
    driver.get("https://www.entrata.com");
    String title = driver.getTitle();
    Assert.assertTrue(title.contains("Entrata"), "Page title should contain Entrata");
  }

  @Test(priority = 2)
  public void testNavigateToCareersWithoutSubmission() {
    home.clickCareersLink();
    Assert.assertTrue(driver.getCurrentUrl().contains("careers"));
  }

  @Test(priority = 3)
  public void testFillDemoFormFields() {
    home.openDemoForm();
    home.enterDemoName("Test Name");
    home.enterDemoEmail("test@example.com");
    Assert.assertEquals(home.getDemoEmailValue(), "test@example.com");
  }

  @Test(priority = 4)
  public void testDynamicResidentPortalButton() {
    home.waitForResidentPortalButton();
    Assert.assertTrue(home.isResidentPortalVisible());
  }
}
