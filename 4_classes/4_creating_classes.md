
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

