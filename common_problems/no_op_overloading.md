# No Operator Overloading

In case you are dealing with vector math, it can be very unfortunately that JavaScript doesn't support `operator overloading` out of box. This can be a powerful feature when used right. By definition it allows you to define what operations between given objects do. In case of a sum of vectors you might expect a vector. In vanilla JavaScript you would have to write `a.add(b)`. In a language supporting overloading simply `a + b` would do. This can get very complicated quite fast.

Fortunately it is quite easy to write a transpiler that provides this functionality for us. I have [covered how to achieve operator overloading](http://www.nixtu.info/2011/05/using-jsshaper-to-provide-operator.html) at my blog. The solution uses a tool known as [JSShaper](http://jsshaper.org/). It is a transformation tool that gives access to JavaScript AST. In this case it is a matter of replacing operators with function calls and defining functions. This little hack allows us to overload the behavior based on types of the operands provided.

This is just one small example of how to extend the language to suit your purposes better. The main disadvantage of JSShaper is that it works only on valid JavaScript syntax. As a result you cannot implement custom language constructs as there is no way to extend AST. In case you can get away by doing some transformation within the current definition, you should be alright.