# opp-projject
#include <iostream>
#include<vector>


// Base class Shape

class Shape {
public:
    virtual double calculateArea() const = 0;  // Pure virtual function for abstraction
    virtual void display() const = 0;
};

// Derived class Circle

class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) : radius(r) {}

    double calculateArea() const override {
        return 3.14159 * radius * radius;
    }

    void display() const override {
       std:: cout << "Circle with radius " << radius << " has area " << calculateArea() <<std:: endl;
    }
};

// Derived class Rectangle

class Rectangle : public Shape {
private:
    double width;
    double height;

public:
    Rectangle(double w, double h) : width(w), height(h) {}

    double calculateArea() const override {
        return width * height;
    }

    void display() const override {
        std::cout << "Rectangle with width " << width << " and height " << height << " has area " << calculateArea() << std::endl;
    }
};

int main() {
    // Creating objects
    
    Circle circle(5.0);
    Rectangle rectangle(4.0, 6.0);

    // Polymorphism: Using a common interface for different objects
    
    std::vector<Shape*> shapes = {&circle, &rectangle};

    for (const Shape* shape : shapes) {
        shape->display();
    }

    return 0;
}
