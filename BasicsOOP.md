Basics of Object-Oriented Programming
======

###### Struct vs. Class

- `Struct`: When you need  structured data
- `Class`: When you need methods, inheritance, generics


###### Abstract Base Class
- Cannot have instances of this
- Defines common shape of descendent classes

#### Class Declarations
```cpp
class Bird{
    public:
        Bird();
        Bird (string colour);
        virtual ~Bird();
        void speak() const;
    private:
        string colour;
};
```
###### Remarks

- `virtual` methods can be overidden in inheriting classes
- `pure virtual` methods are required to be implemented in inheriting class

```cpp
//Virtual, needs implementation in base class
virtual ~HashTable();

//Pure Virtual, class containing this is abstract (cannot create object of this class)
virtual int hash (string key) const = 0;
```

#### Method definitions

```cpp
Bird::Bird() : colour("yellow"){}; //ctor with initializer 

/*
Bird::Bird(string col){ //overloading (**)
    colour = col;       
}
*/

//This does not have problem as above; use ctor with initalizer instead
Bird::Bird(string colour) : colour(colour){}; 

Bird::~Bird(){} //dtor

void Bird::speak() const{
    cout << "I am a " << colour << " bird!" << endl;
}

```

###### Remarks
- (**) If parameter name is the same as actual global var,
must use keyword `this->` to specify which one you're using.

```cpp
Bird::Bird(string colour){
    this->colour = colour;
}
```

- `const` placed at the end of speak() limits
the method from changing any variables within in the method

#### Example Program
```cpp
int main(int argc, char* argv[]){
    Bird mb ("maroon");
    Bird yb;            
    Bird* gb = new Bird ("green");
    Bird* pyb = new Bird;
    Bird* bb = gb;
    // bb->colour = "blue"; //will not work because private 

    mb.speak();         //maroon
    yb.speak();         //yellow
    gb->speak();
    pyb->speak();
    bb->speak();

    delete gb;
    delete pyb;
}
```

#### OO Terminalogy

```Member Variable``` (field):  
1. Instance Variable: One per instance of a class
2. Class/```static``` Variable: One per class

```Member Method```:
1. Instance Method: 
    - Operates on ```this``` object
    - Can call other instance methodsdirectly without going through another object
2. Class/```static``` Method: 
    - Cannot call instance methods directly
    - Must go through another object
    - Can call statics methods, touch static class variable directly
    - Can access objects passed to it as a parameter (otherwise, cannot access instance variables
    

Static Variable Example

```cpp
class Bird{
    public:
        Bird();
        Bird (string colour);
        virtual ~Bird();
    private:
        string colour;  //instance var
        static int currNumBirds; //class var
};

int Bird::currNumBirds = 0;

Bird::Bird() : colour("yellow"){
    Bird::currNumBirds++;
};
Bird::Bird(string colour) : colour(colour){
    Bird::currNumBirds--;
};
Bird::~Bird(){ //destructor
    Bird::currNumBirds--;
} 

```

#### Copy Constructors

- Takes a const ref to existing object (of same class)
- Creates a copy of it as a new object

```cpp
class Bird{
    public:
        ...
        Bird (const Bird &b); //copy ctor
        ...
};

Bird::Bird(const Bird &b) : colour(b.colour){ //creates the clone
    currNumBirds++;
}

int main(int argc, char* argv[]){
    Bird mb ("maroon");
    
    Bird mb1 (mb); //copy ctor
    Bird mb2 = mb; //also calls copy ctor
}
```
