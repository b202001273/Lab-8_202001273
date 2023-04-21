# Lab-8_202001273

- Name: Joshi Hemangi Sanjaybhai
- Student ID: 202001273

# Unit Testing with JUnit

## Goal:
- The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

## Lab Exercises

#### 1. Created a new Eclipse project : hemangiLab8, and within the project create a package : hemangiLab8

![image](https://user-images.githubusercontent.com/75674184/233590785-380b4747-1d5f-4441-a483-77c098627b4f.png)


#### 2. Created a class in the package hemangiLab8 for a Boa.
class name : Boa
JUnit Test Case file : BoaTest


<pre>	
package hemangiLab8;;

//represents a boa constrictor
public class Boa {
        private String name;
        private int length; // the length of the boa, in feet
        private String favoriteFood;

        public Boa (String name, int length, String favoriteFood){
                this.name = name;
                this.length = length;
                this.favoriteFood = favoriteFood;
        }
        //returns true if this boa constrictor is healthy
        public boolean isHealthy(){
                return this.favoriteFood.equals("granola bars");
        }
        //returns true if the length of this boa constrictor is
        //less than the given cage length
        public boolean fitsInCage(int cageLength){
                return this.length < cageLength;

        }
}
</pre>

![image](https://user-images.githubusercontent.com/75674184/233591334-cbc9df0e-425a-4d4a-8bc8-5af869a15db3.png)


#### 3. Created junit test case for class Boa - BoaTest and for test method stubs, select both isHealthy() and fitsInCage(int).


#### 4. Added unit tests
- Method annotated with @Before will be run before each test executes.

<pre>
package hemangiLab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
        private Boa jen;
        private Boa ken;

        @Before
        public void setUp() throws Exception {
                jen = new Boa("Jennifer", 2, "grapes");
                ken = new Boa ("Kenneth", 3, "granola bars");
        }
}
</pre>


![image](https://user-images.githubusercontent.com/75674184/233591766-41761cf7-429a-4484-9b1c-86d584b6dcbb.png)


##### 5. Added private fields for jen and ken in the Boa class.

<pre>
private Boa jen;
private Boa ken;
</pre>

- We added private fields for jen and ken to the BoaTest class, and initialized them in the setUp method. We also updated the testIsHealthy and testFitsInCage methods to use these Boa objects for testing.

- Note that the setUp method will be executed before each test method, so any changes made to the Boa objects during a test will not affect the objects used in other tests.
	
	
![image](https://user-images.githubusercontent.com/75674184/233591994-fe25a2cd-6b3e-4096-887f-ad5f2ca2b06e.png)
	
	
#### 6. Adding some test cases - Modified code
- Method annotated with @Test will be run but the order is not guaranteed.


<pre>
package hemangiLab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}

	@Test 
	public void testIsHealthy() {
		//testing isHealthy for 2 objects
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		//testing isHealthy for 2 objects		
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		
		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
		
	}
}
</pre>
	
	
	
![image](https://user-images.githubusercontent.com/75674184/233591994-fe25a2cd-6b3e-4096-887f-ad5f2ca2b06e.png)
	


- In the first test case, we're testing the isHealthy method of the Boa class. We create two Boa objects with different favorite foods, and verify that isHealthy returns false for the first object and true for the second object.
	
- In the second test case, we're testing the fitsInCage method of the Boa class. We create three Boa objects with different lengths, and test whether they fit in cages of different lengths.


#### 7. Running the two test cases - isHealthy() and fitsInCage()	
	
	
![image](https://user-images.githubusercontent.com/75674184/233596968-4cb06165-421b-442f-ad7c-8699ae07415b.png)
		
	
#### 8. Adding a new method to the Boa class - Modified code -
	
<pre>
package hemangiLab8;

//represents a boa constrictor
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	//returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	//returns true if the length of this boa constrictor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
	return this.length < cageLength;
	
	}
	
	public int lengthInInches()
	{
		int LengthInInches=this.length*12;
		return LengthInInches;
	}
}
</pre>
	
	
	
![image](https://user-images.githubusercontent.com/75674184/233596465-b9ce7698-0070-430e-9e67-eb26604689e5.png)

	
#### 9. Adding test cases for it -

<pre>
package hemangiLab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}

	@Test 
	public void testIsHealthy() {
		//testing isHealthy for 2 objects
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		//testing isHealthy for 2 objects		
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		
		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
		
	}	
	
	@Test
	public void testlengthInInches()
	{
		assertEquals(24,jen.lengthInInches());
		assertEquals(36,ken.lengthInInches());
	}
}
</pre>



![image](https://user-images.githubusercontent.com/75674184/233597175-cfea2b2a-d531-4c1e-99f5-ebe8bb09565f.png)


#### 10. Running the test cases -

![image](https://user-images.githubusercontent.com/75674184/233597365-127a96dc-6080-4852-ae98-9f53fad7864d.png)


