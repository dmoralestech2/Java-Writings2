# Java Lambda

Just want to share with you how I understand Java 8 Lambda. I've been learning about it the past couple of months.

What is a lambda? They are anonymous function. Functions with no names. It only contains parameters and function body.

But you may ask, almost everything in Java is an object, how is that possible?

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