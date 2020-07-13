---
title: Code Examples
linktitle: 💻 Code Examples
toc: true
type: docs
date: "2019-11-21"
lastmod: "2020-07-05"
draft: false
menu:
  java_fundamentals:
    parent: Java
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

---
🕮 [**TOC**]({{< ref "/toc.md" >}})

<br>


## Tip Calculator

```java
public class Main {

// Create the Function
	public static double calculateTotalMealPrice(double listedMealPrice, double tipRate, double taxRate) {
		double tip = tipRate * listedMealPrice;
		double tax = taxRate * listedMealPrice;
		double result = listedMealPrice + tip + tax;
		return result;

	}

	public static void main(String[] args) {
// Call the Function
		double groupTotalMealPrice = calculateTotalMealPrice(100, 0.20, 0.08);
		System.out.println("Total meal price for group: $" + groupTotalMealPrice);

		double individualMealPrice = groupTotalMealPrice / 5;
		System.out.println("Total meal price per individual: $" + individualMealPrice);

	}
}



```

```ini
> Total meal price per individual: $25.6
```

<br>

---
<br>

## Salary Calculator

```java
public class Main {

// Create the Function
	public static double salaryCalculator(double hoursPerWeek, double amountPerHour, int vacationDays) {

		if (hoursPerWeek < 0) {
			return -1;
		}
			
		if (amountPerHour < 0) {
			return -1;
		}
			
		double weeklyPaycheck = hoursPerWeek * amountPerHour;
		double unpaidTime = vacationDays * amountPerHour * 8;
		return (weeklyPaycheck * 52) - unpaidTime;
			
	}
		
// Call the Function
	public static void main(String[] args) {
		double salary = salaryCalculator(40, 15, 8);
		System.out.println("Your annual salary is $" + salary);

	}
}

```

```ini
> Your annual salary is $30240.0
```
<br>

---
<br>

## Triangle Instance

```java
// The Triangle Class blueprint

// Constructor method
public class Triangle {

    // Static variable
    static int numOfSides = 3;

    // Non-Static variables
    double base;
    double height;
    double sideLenOne;
    double sideLenTwo;
    double sideLenThree;

    public Triangle(double base, double height, double sideLenOne, double sideLenTwo, double sideLenThree) {
        this.base = base;
        this.height = height;
        this.sideLenOne = sideLenOne;
        this.sideLenTwo = sideLenTwo;
        this.sideLenThree = sideLenThree;
    }

 // Find Area function (not a constructor)
    public double findArea() {
        return (this.base * this.height) / 2;
    }
}
```
<br>

```java
public class Main {

    public static void main(String[] args) {
        Triangle triangleA = new Triangle(15, 8,15, 8, 17);
        Triangle triangleB =  new Triangle(3, 2.598, 3, 3, 3);

        double triangleAArea = triangleA.findArea();
        System.out.println("The area of triangle 'A' is: " + triangleAArea);

        double triangleBArea = triangleB.findArea();
        System.out.println("The area of triangle 'B' is: " + triangleBArea);

        System.out.println("The length of side three (non-static variable) for triangle 'A' is: " + triangleA.sideLenThree);
        System.out.println("The base (non-static variable) for triangle 'B' is: " + triangleB.base);

        System.out.println("'NumOfSides' (static variable) = " + Triangle.numOfSides);

    }
}
```

```ini
> The area of triangle 'A' is: 60.0
> The area of triangle 'B' is: 3.897
> The length of side three (non-static variable) for triangle 'A' is: 17.0
> The base (non-static variable) for triangle 'B' is: 3.0
> 'NumOfSides' (static variable) = 3
```
<br>

---
