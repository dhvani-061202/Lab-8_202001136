# Lab-8_202001136
## IT314-Software Engineering Lab-8
### Unit Testing with JUnit

#### Goal: The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

#### Lab Exercises
1. Create a new Eclipse project, and within the project create a package.

Creating a new Eclipse project lab8_202001136_project and a new package into the project named lab8_package:

![image](https://user-images.githubusercontent.com/104089036/233311648-6546a61d-fa61-4793-8050-c09bf740fbd1.png)

2. Create a class for a Boa. Here’s the code you can use (you may copy/paste):

The class Boa is created first:

![image](https://user-images.githubusercontent.com/104089036/233312917-a8c2d6ea-b331-4fb8-bf8a-20f48d4e71ec.png)

The code for class Boa is given as follows: 

<pre>
// represents a boa constrictor
public class Boa 
{
  private String name;
  private int length; // the length of the boa, in feet
  private String favoriteFood;
  public Boa (String name, int length, String favoriteFood){
    this.name = name;
    this.length = length;
    this.favoriteFood = favoriteFood;
  }
  // returns true if this boa constrictor is healthy
  public boolean isHealthy(){
    return this.favoriteFood.equals("granola bars");
  }
  // returns true if the length of this boa constrictor is
  // less than the given cage length
  public boolean fitsInCage(int cageLength){
    return this.length < cageLength;
  }
}
</pre>

The code is added into the class:

![image](https://user-images.githubusercontent.com/104089036/233313237-3c1005ca-7c51-4c1d-97bb-2555c2710d16.png)

3. Follow the instructions in the JUnit tutorial in the section “Creating a JUnit Test Case in Eclipse”. You’ll be creating a test case for the class Boa. When you’re asked to select test method stubs, select both isHealthy() and fitsInCage(int).

Created a JUnit Test Case named Boa_test:

![image](https://user-images.githubusercontent.com/104089036/233316028-6f832643-1915-40b0-875a-e2f60eef2067.png)

Selecting isHealthy() and fitsInCage(int) for test methods:

![image](https://user-images.githubusercontent.com/104089036/233316333-62c4d4c7-edfc-4509-9968-8f8b41488ea8.png)

![image](https://user-images.githubusercontent.com/104089036/233314540-8aa67788-f19e-4df6-9184-0b3f4d242066.png)


4. Now it’s time to write some unit tests. Notice that the BoaTest class that JUnit created for you contains stubs for several methods. The first stub (for the method setUp()) is annotated with @Before. The @Before annotation denotes that the method setUp() will be run prior to the execution of each test method. setUp() is typically used to initialize data needed by each test. Modify the setUp() method so that it creates a couple of Boa objects, as follows:
<pre>
@Before
public void setUp() throws Exception {
jen = new Boa("Jennifer", 2, "grapes");
ken = new Boa ("Kenneth", 3, "granola bars");
}
</pre>
(You will need to add private fields for jen and ken to the Boa_test class, otherwise the compiler will complain that there are no variables with those names.)

Added private fields for jen and ken to the Boa_test class and modified the setUp() method:
<pre>
private Boa jen;
private Boa ken;

@Before
public void setUp() throws Exception {
jen = new Boa("Jennifer", 2, "grapes");
ken = new Boa ("Kenneth", 3, "granola bars");
}
</pre>

![image](https://user-images.githubusercontent.com/104089036/233317579-1e8bf934-da70-4aa1-9321-89a3c4b6590a.png)

5. JUnit also provided stubs for two test methods, each annotated with @Test. Work on the testIsHealthy() method first. The purpose of this method is to check that the
isHealthy() method in the Boa class behaves the way it’s supposed to. In the JUnit tutorial, read the section on “Writing Tests”. Modify the testIsHealthy() method so that it checks the results of activating the isHealthy() method on the two Boa objects you created in setup(). Likewise, modify the testFitsInCage() method to test the results of that method. Make sure your test is robust; it should check the results when the cage length is less than the length of the boa, when the cage length is equal to the length of the boa, and when the cage length is greater than the length of the boa. Should you write tests for both jen and ken?

Modifying the testIsHealthy() method and testFitsInCage method():
<pre>
@Test
	public void testIsHealthy() {
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}

@Test
  public void testFitsInCage() {
	  assertEquals(false,ken.fitsInCage(2)); //less than size of Boa
		assertEquals(false,ken.fitsInCage(3)); //equal to size of Boa
		assertEquals(true,ken.fitsInCage(4)); //more than the size of Boa
  }
</pre>

Saving the Boa_test file:

![image](https://user-images.githubusercontent.com/104089036/233321621-a4516786-6dbe-4db3-9004-f4ccaf89b7cb.png)

6. Now you can run your tests. Read the section “Running Your Test Case” in the tutorial. Did you get a green bar in the JUnit pane? If you got a red bar, use the output in the JUnit pane to determine which test(s) failed. Fix your tests, and try running the test case again. It’s important to note that a red bar doesn’t necessarily mean that the test case is written incorrectly; it could be that the method that’s being tested isn’t correct. In fact, that’s what unit testing is supposed to do – help us find errors in our code. When a test fails, you need to determine if the error is in the test case itself or in the code it’s testing.

Running the testisHealthy() method:

![image](https://user-images.githubusercontent.com/104089036/233320410-92ba0cfc-6b38-4d99-a97e-683be15c2908.png)

Running the testFitsInCage method:

![image](https://user-images.githubusercontent.com/104089036/233321906-cb79ac46-d55c-4bdd-9df5-a57f51f06a67.png)

7. Add a new method to the Boa class, with this purpose and signature:
<pre>
// produces the length of the Boa in inches
public int lengthInInches(){
// you need to write the body of this method
}
</pre>
Add a new test case to the BoaTest class that tests the lengthInInches() method. Make sure you annotate the new test method with @Test. Run your tests.
