
# Function versus method #

A function and a method look very similar. They both use the `def` keyword. They also have inputs and return outputs. The difference is that a method is inside of a class whereas a function is outside of a class.

# **What is `self`?**

If you instantiate two objects, how does Python differentiate between these two objects?

```python
shirt_one = Shirt('red', 'S', 'short-sleeve', 15)
shirt_two = Shirt('yellow', 'M', 'long-sleeve', 20)

```

That's where `self` comes into play. If you call the `change_price` method on `shirt_one`, how does Python know to change the price of `shirt_one` and not of `shirt_two`?

```python
shirt_one.change_price(12)

```

Behind the scenes, Python is calling the `change_price` method:

```python
defchange_price(self, new_price):

        self.price = new_price

```

`Self` tells Python where to look in the computer's memory for the `shirt_one` object. Then, Python changes the price of the `shirt_one` object. When you call the `change_price` method, `shirt_one.change_price(12)`, `self` is implicitly passed in.

The word `self` is just a convention. You could actually use any other name as long as you are consisten, but you should use `self` to avoid confusing people.

![image](https://user-images.githubusercontent.com/7238176/126899651-e3992616-d376-4f65-b99b-ae567615d5de.png)

Syntax to create a new shirt object. The yntax order matches the init method. **This is called instantiating an object**.
Syntax and order match the init method. I am initializing this specific shirt with the attributes. Python is going to call the init method to initialize this shirt object.

Initializing the t-shirt:running the function, we have an output object. The output is a shirt object, and all the letters and numbers is python giving the location and memory where the object is stored. But this isn't very useful unless we store the object in a variable. So in the next slide, we will store the object in a variable. Shirt object will stored in the variable new shirt. The new shirt variable has a color, size, style and price associated with it. You can access these attributes using the dot syntax. 

Scrolling down, you use the same dot syntax to access the methods as well, except, you also need to specify any inputs that these methods require. For example, to change the price, I call the change_price method with a value of 10. Running this code you can see that the price changed from 15 to 10. The same goes for the discount method.  

![image](https://user-images.githubusercontent.com/7238176/126899809-3a420f50-87be-4079-95c6-12f6097c4a5d.png)

In the last part, I instantiate three shirt objects, and stored those objects in a list. These variables are like any other python variable.  Once he stored the shirts into the tshirt_collection list, he then ran a for loop to print out the color of each shirt. 

![image](https://user-images.githubusercontent.com/7238176/126899834-738894a8-c6cc-4bde-969a-a629db84a168.png)

![image](https://user-images.githubusercontent.com/7238176/126900579-435e1bc6-b7cf-445c-833a-e561fe465c40.png)

![image](https://user-images.githubusercontent.com/7238176/126900650-8aae74ef-df58-4767-b7db-c2e5d0afb2d6.png)

Converting everything from dollars to euros at the method value (not attributes, which you would have to do one by one, manually)

![image](https://user-images.githubusercontent.com/7238176/126900788-ae5fbc3b-e356-4f26-90e4-35ce6e467499.png)

![image](https://user-images.githubusercontent.com/7238176/126900812-6cbe1389-d186-4cd2-bcab-cbd754e9314e.png)

Notes about OOP

Set and get methods
The last part of the video mentioned that accessing attributes in Python can be somewhat different than in other programming languages like Java and C++. This section goes into further detail.

The Shirt class has a method to change the price of the shirt: shirt_one.change_price(20). In Python, you can also change the values of an attribute with the following syntax:

````shirt_one.price = 10
shirt_one.price = 20
shirt_one.color = 'red'
shirt_one.size = 'M'
shirt_one.style = 'long_sleeve'```

This code accesses and changes the price, color, size, and style attributes directly. Accessing attributes directly would be frowned upon in many other languages, but not in Python. Instead, the general object-oriented programming convention is to use methods to access attributes or change attribute values. These methods are called set and get methods or setter and getter methods.

A get method is for obtaining an attribute value. A set method is for changing an attribute value. If you were writing a Shirt class, you could use the following code:

```class Shirt:

    def __init__(self, shirt_color, shirt_size, shirt_style, shirt_price):
        self._price = shirt_price

    def get_price(self):
      return self._price

    def set_price(self, new_price):
      self._price = new_price```
      
Instantiating and using an object might look like the following code:

```shirt_one = Shirt('yellow', 'M', 'long-sleeve', 15)
print(shirt_one.get_price())
shirt_one.set_price(10)```

In the class definition, the underscore in front of price is a somewhat controversial Python convention. In other languages like C++ or Java, price could be explicitly labeled as a private variable. This would prohibit an object from accessing the price attribute directly like shirt_one._price = 15. Unlike other languages, Python does not distinguish between private and public variables. Therefore, there is some controversy about using the underscore convention as well as get and set methods in Python. Why use get and set methods in Python when Python wasn't designed to use them?

At the same time, you'll find that some Python programmers develop object-oriented programs using get and set methods anyway. Following the Python convention, the underscore in front of price is to let a programmer know that price should only be accessed with get and set methods rather than accessing price directly with shirt_one._price. However, a programmer could still access _price directly because there is nothing in the Python language to prevent the direct access.

To reiterate, a programmer could technically still do something like shirt_one._price = 10, and the code would work. But accessing price directly, in this case, would not be following the intent of how the Shirt class was designed.

One of the benefits of set and get methods is that, as previously mentioned in the course, you can hide the implementation from your user. Perhaps, originally, a variable was coded as a list and later became a dictionary. With set and get methods, you could easily change how that variable gets accessed. Without set and get methods, you'd have to go to every place in the code that accessed the variable directly and change the code.

You can read more about get and set methods in Python on this Python Tutorial site.

Attributes
There are some drawbacks to accessing attributes directly versus writing a method for accessing attributes.

In terms of object-oriented programming, the rules in Python are a bit looser than in other programming languages. As previously mentioned, in some languages, like C++, you can explicitly state whether or not an object should be allowed to change or access an attribute's values directly. Python does not have this option.

Why might it be better to change a value with a method instead of directly? Changing values via a method gives you more flexibility in the long-term. What if the units of measurement change, like if the store was originally meant to work in US dollars and now has to handle Euros? Here's an example:

Example: Dollars versus Euros
If you've changed attribute values directly, you'll have to go through your code and find all the places where US dollars were used, such as in the following:

```shirt_one.price = 10 # US dollars```

Then, you'll have to manually change them to Euros.

```shirt_one.price = 8 # Euros```

If you had used a method, then you would only have to change the method to convert from dollars to Euros.


```def change_price(self, new_price):
    self.price = new_price * 0.81 # convert dollars to Euros```

```shirt_one.change_price(10)```
For the purposes of this introduction to object-oriented programming, you don't need to worry about updating attributes directly versus with a method; however, if you decide to further your study of object-oriented programming, especially in another language such as C++ or Java, you'll have to take this into consideration.

Modularized code
Thus far in the lesson, all of the code has been in Jupyter Notebooks. For example, in the previous exercise, a code cell loaded the Shirt class, which gave you access to the shirt class throughout the rest of the notebook.

If you were developing a software program, you would want to modularize this code. You would put the Shirt class into its own Python script, which you might call shirt.py. In another Python script, you would import the Shirt class with a line like from shirt import Shirt.

For now, as you get used to OOP syntax, you'll be completing exercises in Jupyter Notebooks. Midway through the lesson, you'll modularize object-oriented code into separate files.






