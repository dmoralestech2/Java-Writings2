# Java Lambda

Just want to share with you how I understand Java 8 Lambda. I've been learning about it the past couple of months.

My purpose here is to make you up to speed in using lambdas in your project. And hopefully convince you to use it.

Let's get into it.

What is a lambda? Lambdas are anonymous functions. Functions with no names. It only contains parameters and function body.

If you want to picture it, just imagine a function like:
```
\\Normal function
public void greetName(String name) {
    System.out.println("Hello " + name);
}

And then you remove the function name and everything before that, like so
```
\\ A primitive lambda - which is not too far away from the real thing!
(String name) {
    System.out.println("Hello " + name);
}
```

So what's good about it?
- the beauty about lambdas is you can assign it to a variable and treat it like a variable. This also means you can pass it around as a parameter, etc...

- you can do some

Why is it useful? Why do I need to know this?

But you may ask, almost everything in Java is an object, how will this be possible?

In Java the way they achieve this is by wrapping it in a class with only 1 method. And it implement a Functional Interface.

And Java provides a syntactic sugar so that *it hides* the class and method implementations and only show you the parameters and function body.

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

Test commit
