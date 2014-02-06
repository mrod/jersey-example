jersey-example
==============

 - We use @Path("/helloWorldREST") annotation in the class definition. This means that HelloWorldREST REST service can be reached in the URL .../helloWorldREST.
 - In that URL, all GET requests are going to be handled by responseMsg method which is annotated with @GET.
 - In this example we explore two ways to pass parameters in a GET request in REST services. One of them is URI path parameters. We define this parameter with @Path("/{parameter}") annotation on responseMsg method. For example, to pass “JavaCodeGeeks” as the value of a path parameter, called parameter, we should follow .../helloWorldREST/JavaCodeGeeks URL. Now, to parse that parameter we have to declare an argument to the method that will handle the request, in our case that is responseMsg. The way to parse path parameters is by using @PathParam annotation in the argument of the method. In this case the parameter will be parsed as a String. If you try to follow .../helloWorldREST URL you will get HTTP Status 405 - Method Not Allowed, as responseMsg will only handle requests in the form of .../helloWorldREST/{any_value}.
 - The second way to pass parameter is Query parameters. For example, to pass “Enjoy” as a value of a query parameter, called value, one should follow .../helloWorldREST/{any_value}?value=Enjoy URL. 
 - Now, to parse that parameter we have to declare an argument to the method that will handle the request, in our case that is responseMsg. The way to parse query parameters is by using @QueryParam annotation in the argument of the method. 
 - In this case the parameter will be parsed as a String. If you try to follow .../helloWorldREST/{any_value} the value parameter cannot be parsed and you would get a HTTP 400 (Client Error) error. This is why you can use @DefaultValue, to define a default value for the parameter and thus the service will be always available even if the request URI does not contain the corresponding query string.
 - If all parameters are parsed correctly, the URI path parameter will be available to  responseMsg through parameter variable, and query parameter will be available to  responseMsg through value variable.

@QueryParam and @PathParam can only be used on the following Java types:

 - All primitive types except char
 - All wrapper classes of primitive types except Character
 - Have a constructor that accepts a single String argument
 - Any class with the static method named valueOf(String) that accepts a single String argument
 - Any class with a constructor that takes a single String as a parameter
 - List<T>, Set<T>, or SortedSet<T>, where T matches the already listed criteria. Sometimes parameters may contain more than one value for the same name. If this is the case, these types may be used to obtain all values.
