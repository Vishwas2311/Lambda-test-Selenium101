# Lambda-test-Selenium101

Test Scenario 1:


System.setProperty("webdriver.chrome.driver","V:\\chromedriver_win32\\chromedriver.exe");
	WebDriver driver=new ChromeDriver();
	driver.get("https://www.lambdatest.com/selenium-playground/");
	driver.findElement(By.xpath("//a[.='Simple Form Demo']")).click();
	
	String name1 ="Simple Form Demo";
	String link1 = driver.findElement(By.xpath("//a[.='Simple Form Demo']")).getText();
	
	Assert.assertEquals(link1, name1);	
	
	
	String veriable = "Welcome to LambdaTest";
	driver.findElement(By.xpath("//input[@id='user-message']")).sendKeys(veriable);
	driver.findElement(By.cssSelector("button[id='showInput']")).click();
	
	//relative locator below
    WebElement massage=driver.findElement(By.xpath("//label[.='Your Message: ']"));		
	String veriable1 =driver.findElement(with(By.cssSelector("p[id='message']")).below(massage)).getText();
	Assert.assertEquals(veriable, veriable1);
	
	
  
  
  
  Test Scenario 2:
  
  
  
  
  
  
	System.setProperty("webdriver.chrome.driver", "V:\\chromedriver_win32\\chromedriver.exe");
	WebDriver driver =new ChromeDriver();
	driver.manage().window().maximize();
	driver.get("https://www.lambdatest.com/selenium-playground/input-form-demo");
	
	driver.findElement(By.xpath("//div/p[contains(text(),'Progress Bar & Sliders')]")).click();
	driver.findElement(By.cssSelector("a[href*='https://www.lambdatest.com/selenium-playground/drag-drop-range-sliders-demo']")).click();
	
	//here we need to find the X & y coordinate of the page where we need to drop the pointer
	//We will use the "PageRuler" Extension for the chrome.
	Actions slider=new Actions(driver);
	//giving X & Y coordinate with "PageRuler"
	slider.moveByOffset(754, 609).click().build().perform();
	String actual=driver.findElement(By.id("rangeSuccess")).getText();
	String expected ="95";
	Assert.assertEquals(actual, expected);
	
	
	
  
  
  
  Test Scenario 3:
  
  
  
  
  
  
  System.setProperty("webdriver.chrome.driver", "V:\\chromedriver_win32\\chromedriver.exe");
		WebDriver driver =new ChromeDriver();
		driver.manage().window().maximize();
		driver.get("https://www.lambdatest.com/selenium-playground/input-form-demo");
		driver.findElement(By.xpath("//button[contains(.,'Submit')]")).click();
		
		
		JavascriptExecutor js= (JavascriptExecutor)driver;

		WebElement field =driver.findElement(By.name ("name"));

		Boolean isvalid = (Boolean)js.executeScript("return arguments[0].checkValidity();", field); 
		String message =(String)js.executeScript("return arguments[0].validationMessage;", field); 
		String expected= "Please fill out this field.";
		//String message=driver.findElement(By.name("name")).getAttribute("validationMaessage");
		System.out.println(message);
		Assert.assertEquals(message, expected);
		
	    driver.findElement(By.id("name")).sendKeys("vishwas");
	    driver.findElement(By.id("inputEmail4")).sendKeys("Vishwasshinde745@gmai.com");
	    driver.findElement(By.id("inputPassword4")).sendKeys("Vishwas1234");
	    driver.findElement(By.id("company")).sendKeys("RedHat");
	    driver.findElement(By.id("websitename")).sendKeys("www.google.com");
	    driver.findElement(By.id("inputCity")).sendKeys("Pune");
	    driver.findElement(By.id("inputAddress1")).sendKeys("Vimannagar");
	    driver.findElement(By.id("inputAddress2")).sendKeys("kharadibypass");
	    driver.findElement(By.id("inputState")).sendKeys("Maharashtra");
		driver.findElement(By.id("inputZip")).sendKeys("422605");
		
		//using "SELECT" Class
		driver.findElement(By.name("country")).click();
		WebElement Countries=driver.findElement(By.name("country"));
		Select country =new Select(Countries);
		country.selectByVisibleText("United States");
		driver.findElement(By.xpath("//button[.='Submit']")).click();
		
		//massage validating
		String successful="Thanks for contacting us, we will get back to you shortly.";
		//Grabbing text
		String message2=driver.findElement(By.xpath("//p[@class='success-msg hidden']")).getText();
		System.out.println(message2);
		Assert.assertEquals(successful, message2);
  
  
  
