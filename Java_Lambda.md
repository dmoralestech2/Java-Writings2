# Java Lambda

Just want to share with you how I understand Java 8 Lambda. I've been learning about it the past couple of months.

My purpose here is to bring you up to speed in using the lambda features of Java 8 in your project.

Let's get into it.

What is a lambda? In simple java term, Lambdas are functions with no name.  They are also called anonymous functions. It only contains parameters and function body.  If you want to picture it, just imagine a function like:
```Java
\\Normal function
public void greetName(String name) {
    System.out.println("Hello " + name);
}
```

And then you remove the function name and everything before that, like so:
```Java
\\ A primitive lambda - which is not too far away from the real thing!
(String name) {
    System.out.println("Hello " + name);
}
```

So what's good about it?
- The beauty about lambdas is you can assign it to a variable and treat it like a variable. This also means you can pass it around as a parameter, return it from a function, store it in an array or a collection, etc...  It's another way of abstraction.

In our example above converting it to a proper Java lambda it would be:
```Java
name -> System.out.println("Hello " + name);
```

And since it's a function with no name, you're not limited to only one line:
```Java
name -> { 
            System.out.println("Hello " + name);
            System.out.println("Some other text...");
            System.out.println("Have a nice day");
        };
```

and you can assign it in a variable:
```Java
Consumer<String> helloGreeter = name -> System.out.println("Hello " + name);
Consumer<String> hiGreeter = name -> { 
                                            System.out.println("Hi " + name); 
                                            System.out.println("How you doin?"); 
                                        };
```
A good analogy of a lambda is to think of it as a block of code and you can treat as a variable.

Notice the ```Consumer<String>``` object type? Understanding that is the key to understanding lambdas and using it straight away!

So what is that ```Consumer<String>```? If you go to it's declaration:
```Java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}    
```

It's only an interface with one method that accepts a type and returns nothing, and it has a @FunctionalInterface annotation.

Why is it a good thing? 
- Generally, it would make your code shorter/less verbose. A lot more expressive and cleaner.

The secret in using lambdas straight-away in Java is having a good understanding of Functional Interface. Remember that almost everything in Java is an Object? This is how Java wraps those anonymous functions that were created into objects.




But you may ask, almost everything in Java is an object, how will this be possible?

In Java the way they achieve this is by wrapping it in a class with only 1 method. And it implement a Functional Interface.

And Java provides a syntactic sugar so that *it hides* the class and method implementations and only show you the parameters and function body.

So how did it come up like this?

Remember in Java almost everything is an object. In this case here, Java is wrapping this up in an object under the hood.

Java would probably wrap it similar to this:
```Java
    class SomeRandomGeneratedClassName<String> implements Consumer<String>{
        @Override
        public void accept(String name) {
            System.out.println("Hello " + name);
        }
    }
```

And how will Java know it will convert it to a Lambda? The secret is in 




@FunctionalInterface tells Java that you want to use lambda.

For me the key in learning Lambdas is understand Functional Interfaces and how to use them.

```Java
        Consumer<String> consumerSample = (new Consumer<String>() {
            @Override
            public void accept(String s) {
                doSomeWork();
            }
        });

        Consumer<String> consumerSample2 = s -> doSomeWork() ;

        Supplier<String> supplierSample = (new Supplier<String>() {
            @Override
            public String get() {
                return "returns some string..";
            }
        });
        
        Supplier<String> supplierSample2 = () -> "returns some string...";        

```

Everything in Java is still an object and Java Lambda is also an object

If you look into the parameters, it's still asking for an object of type Supplier. And Supplier is an interface with only one method that has a specific signature.

The key to understanding Functional Interfaces is to understand their method signatures.

When I see an interface with a @FunctionInterface annotation I think of it as one method wrapped in an object.

If we see a parameter of type interface, it means that we need to pass an object that implements that interface.