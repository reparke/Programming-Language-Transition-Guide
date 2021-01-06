
## Creating Class Definitions

### Class definition: C++ ([Order.h](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/c%2B%2B/order.h))

```c++
/*
Rob Parke
Viterbi School of Engineering
University of Southern California
Java, C++, and Python Review
*/

// This file defines the prototype (aka outline) of the Order class
 
#pragma once      // Required at the top of new header (.h) files

public class Order {
  // variables declaration
  private:
    String name;
    int pounds;
    double costPerPound;
  
  public:
    //default constructor
    Order();
    
    // get / set methods
    string getName();
    int getPounds();
    double getCostPerPound();
    
    void setName(string newName);
    void setPounds(int newPounds);
    void setCostPerPound(double newCostPerPound);
    
    // methods
    /* calcCost
     * input: none
     * output: returns pounds * costPerPound
     */
    double calcCost();
    
    /* displayOrder
     * input: none
     * output: none
     * side-effect: prints a summary of the order to the screen
     */
    void displayOrder();
}
```

### Class Implementation: C++ ([order.cpp](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/c%2B%2B/order.cpp))
```c++
/*
Rob Parke
Viterbi School of Engineering
University of Southern California
Java, C++, and Python Review
*/


//default constructor
Order::Order() {
  name = "";
  pounds = 0;
  costPerPound = 0.0;
}

// get / set methods
string Order::getName(){ return name;   }
int Order::getPounds() { return pounds; }
double Order::getCostPerPound() { return costPerPound;   }

void Order::setName(string newName) { name = newName;   }
void Order::setPounds(int newPounds) {  pounds = newPounds;  }
void Order::setCostPerPound(double newCostPerPound){ costPerPound = newCostPerPound;
}

// methods
/* calcCost
 * input: none
 * output: returns pounds * costPerPound
 */
double Order::calcCost(){
  return pounds * costPerPound;
} 

/* displayOrder
 * input: none
 * output: none
 * side-effect: prints a summary of the order to the screen
 */
void Order::displayOrder(){
  cout << "Order: "
	<< name 
	<< " for " 
	<< pounds 
	<< " lbs @ $"
	<< costPerPound
	<< "/lb";
}

```


### Class definition: Python ([Order.py](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/python/order.py))

```python
class Order(object):
  # default constructor
  def __init__(self):
    # create instance variables for the objects
    self.__name = ""
    self.__pounds = 0
    self.__costPerPound = 0.0
	
	# get / set methods
  def getName(self):
    return self.__name

  def getPounds(self):
    return self.__pounds

  def getCostPerPound(self):
    return self.__costPerPound

  def setName(self, newName):
    self.__name = newName

  def setPounds(self, newPounds):
    self.__pounds = newPounds

  def setCostPerPound(self, newCostPerPound):
    self.__costPerPound = newCostPerPound


  # methods
  '''
   calcCost
   input: none
   output: returns pounds * costPerPound
  '''
  def calcCost(self):
    return self.__pounds * self.__costPerPound


  '''
   displayOrder
   input: none
   output: none
   side-effect: prints a summary of the order to the screen
  '''
  def displayOrder(self):
    print("Order: " + self.__name + " for " +
        str(self.__pounds) + " lbs @ $" +
        str(self.__costPerPound) + "/lb")
```



### Class definition: Java ([Order.java](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/java/Order.java))

```java
public class Order {
  // variables declaration
  private String name;
  private int pounds;
  private double costPerPound;
  
  //default constructor
  public Order() {
    name = "";
    pounds = 0;
    costPerPound = 0.0;
  }
  
  // get / set methods
  public String getName(){ return name;   }
  public int getPounds() { return pounds; }
  public double getCostPerPound() { return costPerPound;   }
  
  public void setName(String newName) { name = newName;   }
  public void setPounds(int newPounds) {  pounds = newPounds;  }
  public void setCostPerPound(double newCostPerPound){ costPerPound = newCostPerPound;
  }
  
  // methods
  /* calcCost
   * input: none
   * output: returns pounds * costPerPound
   */
  public double calcCost(){
    return pounds * costPerPound;
  } 
  
  /* displayOrder
   * input: none
   * output: none
   * side-effect: prints a summary of the order to the screen
   */
  public void displayOrder(){
    System.out.println("Order: " + name + " for " + pounds +
              " lbs @ $" + costPerPound + "/lb");
  }
}
```

## Using Classes to Create Objects

### Using classes: C++ ([driver.cpp](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/c%2B%2B/driver.cpp))

```c++
/*
Rob Parke
Viterbi School of Engineering
University of Southern California
Java, C++, and Python Review
*/


/*
Classes concept
  Very similar to Java / Python with most syntax changes
  
  Class can contain instance variables and instance methods
  Methods and variables can have an access level (public, private, or protected)
 
Definition
  As in Java / Python, classes are defined in a block of code and begin with the word "class"
 
  Class definitions end with a SEMI-COLON;
 
Constructor
  The constructor method always has the same name as the class
 
  Python: There is no __init__.  Instead, the class name serves as the constructor.
    For instance, the class "Coffee" would have a constructor called
    Coffee()
 
Public / Private and declaring instance variables
  Classes in C++ have a public and private section.
  Within each section you specify all the methods and variables that are either public or private
 
  For example, if a class has private int variable foo and public methods getFoo and setFoo, use
    private:
      int foo;
    public:
      int getFoo()
        ...
      void setFoo(int num)
        ...
 
  Java: You do not specify "public" or "private" for every variable / method.
    Rather, you include all relevant variables / methods with section.

  Python: A major difference in C++ is that you MUST define all instance variables
    in the class defintion (i.e. OUTSIDE of the constructor).
    For example, instead of creating private variale "self.__foo" in __init__,
      you instead use "int foo" in the private section of the class.
    This follows the C++ principle that you must define ahead of time all
      variables / functions before using them
 
Parameters by value vs. by reference
  When parameters are passed to functions, there are two primary options:
    - If a parameter is passed by value, a copy of the parameter is passed
      to the function. Generally, basic types (such as int, double, etc)
      should be passed by value.
    - If a parameter is passed by reference, the variable is handed off to the
      class, and no copy is made. Generally, object types (such as std::string,
      and custom classes) should be passed by reference.
    ** A major exception to this is arrays. Arrays are never copied, and are
      more or less "automatically" passed by reference
  
  We have been passing parameters by value in our functions so far. So for
    example, calcSquare takes in the parameter num by value:
      int calcSquare(int num)
      {
        return num * num;
      }
 
  To pass a parameter by reference, an ampersand & is placed between the type and the
    parameter name. So for example, this function takes in a std::string by reference:
      void printString(std::string& toPrint)
      {
        std::cout << toPrint << std::endl;
      }
 
Note: In this example, we declare our class and use it in the same file.
  Typically, this is not the case and we create separate .h/.cpp files for each class
  (as in the Inheritance example #5).
 
As with functions, classes must be declared before any code that uses them.
 
*/

#include "Order.h"  // This is our custom Rectangle 
#include <iostream>    //needed for cin / cout
#include <string>    //needed for strings


// function prototype
void finalizeOrder(Order& newOrder) // Pass by reference!
{
  double cost = 0;
  
  newOrder.displayOrder();
  cost = newOrder.calcCost();
  std::cout << "Your order costs $" << cost;
  
}

int main() {
  //const means the variable is a CONSTANT and can not change
  const double COST_PER_POUND = 7.99;

  //create an order object
  //Java: note we do not use NEW in the basic case of constructing
  // a class as a local variable
  Order order1;
  std::string tempName = "";
  int tempPounds = 0;
  
  std::cout << "Enter coffee name (one word please): ";
  std::cin >> tempName;
  order1.setName(tempName);

  std::cout <<"Enter # of pounds: ";
  std::cin >> tempPounds;
  order1.setPounds(tempPounds);

  order1.setCostPerPound(COST_PER_POUND);

  finalizeOrder(order1);

  std::cout << std::endl << std::endl;

  return 0;
}
```



### Using classes: Python ([main.py](https://github.com/reparke/Programming-Language-Transition-Guide/blob/main/4_classes/python/main.py))

```python
# import Order class
from Order import Order

# define CONSTANT
COST_PER_POUND = 7.99

# define main function
def main():

  order1 = Order()
  tempName = ""
  tempPounds = 0

  tempName = input("Enter coffee name (one word please): ")
  order1.setName(tempName)

  tempPounds = int(input("Enter # of pounds: "))
  order1.setPounds(tempPounds)

  order1.setCostPerPound(COST_PER_POUND)

  finalizeOrder(order1)



def finalizeOrder(newOrder):
  cost = 0

  newOrder.displayOrder()
  cost = newOrder.calcCost()
  print("Your order costs $" + str(cost))



# call main function
main()
```



### Using classes: Java

```java
/*
Rob Parke
Viterbi School of Engineering
University of Southern California
Java, C++, and Python Review
*/

import java.util.Scanner;
public class Program {

  public static void main(String[] args) {
    final double COST_PER_POUND = 7.99;
    
    Scanner input = new Scanner(System.in);
    Order order1 = new Order();
    String tempName = "";
    int tempPounds = 0;
    
    System.out.println("Enter coffee name (one word please): ");
    tempName = input.next();
    order1.setName(tempName);
    
    System.out.println("Enter # of pounds: ");
    tempPounds = input.nextInt();
    order1.setPounds(tempPounds);
    
    order1.setCostPerPound(COST_PER_POUND);

    finalizeOrder(order1);
    
  }
  
  public static void finalizeOrder(Order newOrder){
    double cost = 0;
    
    newOrder.displayOrder();
    cost = newOrder.calcCost();
    System.out.println("Your order costs $" + cost);
    
  }
}
```
