# Java_OOP
basics of java and opps concepts
**S.O.L.I.D**
S — Single responsibility principle
O — Open closed principle
L — Liskov substitution principle
I — Interface segregation principle
D — Dependency Inversion principle


# Java_OOP
basics of java and opps concepts
**S.O.L.I.D DESIGN PRINCIPLES** 
S - Single Responsibility Principle (known as SRP)
O - Open/Closed Principle
L - Liskov’s Substitution Principle
I - Interface Segregation Principle
D - Dependency Inversion Principle

Single Responsibility
-------------------------
“class should be having one and only one responsibility”. What does it mean? 
A class or module should have only one reason to change.

What is Responsibility
Responsibility is the work or action that each part of your system, the methods, the classes, the packages, the modules are assigned to do.
Too much responsibility leads to coupling.

For example(1)
lets say we have a User Class that we keep some info in there.
class User {
  public age;  
  public name;
  public slug;
  public email;
}

It does make sense to keep only methods that set or get the role, name, age properties.
However, if we decided to add some other methods:
class User {
  public age;  
  public name;
  public slug;
  public email;
  // Xmm why do we have them here?
  checkAge();
  validateEmail();
  slugifyName();
}
Those checkAge, validateEmail, slugifyName look strange for sure.

That would actually make the class less cohesive as it would assign those methods that make no sense to have in a User class. It could be extracted in a different class for example UserFieldValidation.


ex-3
class Employee
{
public Money calculatePay()
public void save()
public String reportHours()
}
This class violates the SRP because it has three reasons to change:
The business rules having to do with calculating pay.
The database schema.
The format of the string that reports hours.

-We don't want a single class to be impacted by these three completely different forces. We don't want to modify the Employee class every time the accounts decide to change the format of the hourly report, or every time the DBAs make a change to the database schema, as well as every time the managers change the payroll calculation. Rather, we want to separate these functions out into different classes so that they can change independently of each other.

**solution**
-Gather together the things that change for the same reasons. Separate those things that change for different reasons.
-Keep track of the dependencies by checking for example if a constructor has too many input parameters thus many dependencies. If it’s possible always inject them via DI.
Use Dependency Injection
-Isolate change by looking closely at the things that make the whole and separate them logically. You need to be aware of your code and why does is written that way. Always look for a too big method or function.
-Keep track of method parameters as it denotes that the method may be required on many things in order to function.
-Use simple naming as it will help you refactor the code for single responsibility. Long function names imply that there is something fishy there.
-Refactor early and as often as you see that something can be simplified. This will help you with tidying up you code on the go.

ex-4
Well let’s take the class A which does the following operations.
1)Open a database connection
2)Fetch data from database
3)Write the data in an external file

The issue with this class is that it handles lot of operations. Suppose any of the following change happens in future.
The issue with this class is that it handles lot of operations. Suppose any of the following change happens in future.
•	New database
•	Adopt ORM to manage queries on database
•	Change in the output structure
So in all the cases the above class  would be changed. Which might affect the implementation of the other two operations as well. So ideally according to SRP there should be three classes each having the single responsibility.



Ex2- 
class 1-  EmployeePayroll
class2-EmployeeLeave
class3-EmployeTimeSheet    
as the above 3 classed are doing only 1 thing they all follow single responsibility principle, if in future you want to make some change you know where to make changes.
