**What is module?**
ans: 
Module is an independent separable component or part of a system(software or hardware).

**What is modularity?**
In software engineering, 
modularity refers to the extent to which a software/Web application may be divided into smaller modules.
here modules are capable of serving a specified business domain.
example: search for trains avilability, book the ticket, payment, etc. 

**Why modularity?**
We use modularity to change subcomponents of the system without affecting whole system.
We use Modularity to enable re-usability and to minimizes duplication.
we use modularity to make multiple modules first and then link and combine them to form a complete system.

**What is modular architecture?**
Modular Architecture is exactly what you think it is — a way to manage the complexity of a problem by breaking them down to smaller manageable modules.
Modules are separate components those can be connected together.

The beauty of modular architecture is that you can replace or add any one component (module) without affecting the rest of the system. 

Modular Architecture, as a style, helps us view the system, not just in layers or services, but goes one level below as composition of smaller, physical modules.

 Modular Architecture defines module as a “deployable, manageable, natively reusable, composable, stateless unit of software that provides a concise interface to consumers”.
 
 In Java, a JAR file represents the essence of a module.

These modules have clear business context, confines them to enclosing physical layer, works within the context that they are provided and express their scope through a public interface. 

They help us in understanding, extending and managing the system during design and during run time, that is, design time modularity and run time modularity.



**Modularity in software development can be boiled down into three guiding principles:**

**1. Strong encapsulation:** hide implementation details inside components, leading to low coupling between different parts. Teams can work in isolation on decoupled parts of the system.
  So A key motivation of the module system is strong encapsulation.

**2. Well-defined interfaces:** you can't hide everything (or else your system won't do anything meaningful), so well-defined and stable APIs between components are a must. A component can be replaced by any implementation that conforms to the interface specification.

**3. Explicit dependencies:** having a modular system means distinct components must work together. You'd better have a good way of expressing (and verifying) their relationships.

The focus of modular architecture is how you design the physical composition of the application.

Many of these principles can be realized with microservices. A microservice can be implemented in any way, as long as it exposes a well-defined interface (oftentimes a REST API) for other services. Its implementation details are internal to the service, and can change without system-wide impact or coordination. Dependencies between microservices are typically not quite explicit at development-time, leading to possible service orchestration failures at run-time. Let's just say this last modularity principle could use some love in most microservice architectures.

So, microservices realise important modularity principles, leading to tangible benefits:

Teams can work and scale independently.
Microservices are small and focused, reducing complexity.
Services can be internally changed or replaced without global impact.
What's not to like? Well, along the way you've gone from a single (albeit slightly obese) application to a distributed system of microservices. This brings an enormous amount of operational complexity to the table. Suddenly, you need to continuously deploy many different (possibly containerized) services. New concerns arise: service discovery, distributed logging, tracing and so on. You are now even more prone to the fallacies of distributed computing. Versioning of interfaces and configuration management become a major concern. The list goes on and on.

It turns out there is as much complexity in the connections between microservices as there is in the combined business logic of all individual microservices. And to get here, you can't just take your monolith and chop it up. Whereas 'spaghetti code' in monolithic codebases is problematic, putting a network boundary in between escalates these entanglement issues to downright painful.

### Java 9 Modularity

### What and Why

1) Maintainability is one of the most significant concerns in software design and evolution.

We want a code base that is loosely coupled, highly cohesive, extremely readable, and can be understandable at a glance.

We design our classes and organize them in packages.

So far so good, but when we have hundreds of packages, the dependencies between them are not visible at one look.
Therefore, we need something more than packages to organize our code base to make it more maintainable.

2) Another problem is the Java classpath and how it runs our codes.

All JAR classes and libraries are flattened into the classpath.

When these JAR files have multiple version of a class on the runtime, the Java ClassLoader can load only one version of that class. In this way, there is ambiguity about how your program is going to work, and ambiguity is a bad thing.

This issue is so frequent that you might know it as “JAR Hell.”

3) Another problem with the classpath is that it doesn’t follow the “Fail First” principle.

You may have missing classes that exist in the classpath, but not in the production environment.

Until you get the JavaClassDefError exception at runtime, you can’t be sure what is missing.

4) Finally, the big issue with the classpath is encapsulation.

Every class on the classpath has access to each other, and this is an encapsulation violation.

We want to hide our internal APIs, and that’s why we need another level of encapsulation (“Strong Encapsulation”) and control over the access to our classes in our packages.

So finally Modules are going to fix these issues.

#### What is a module in java9?

ans:

A module has a name, it groups related code, and is self-contained.

A module describes explicitly what it needs from other modules and which part of it is visible to other modules.

In this manner, dependencies between modules are crystal clear.

We have Strong Encapsulation, which means we can hide our internal APIs, and finally, we now follow the “Fail First” principle. Therefore, when there is a missing module or a conflict, you will get an error.

Modularizing the JDK allows JDK developers to manage the huge complexity of it.

When you write a tiny and straightforward application that doesn’t use RMI, CORBA, Java EE, and other stuff, why do you need a full, huge, and heavy JRE? Isn’t it wiser to have your runtime image only contain the modules you need? Now with a modularized platform, it’s possible.

![](https://github.com/satyamnvv/ModulartiyPOCS/blob/master/jdk-modules.jpg)

This is how the JDK now looks.
On the bottom, we have the “java.base” module that every other module implicitly or explicitly depends on.
As you can see, this dependency graph is a DAG, which means no circular dependencies allowed.

module-info.java
 module <module-name>{
  exports <package1>;
  exports <package2>;
  exports <package3>;
  .
  .
  .
  requires <module1>;
  requires <module2>;
  requires <module3>;
  .
  .
  .
 }

In the module-info.java file, you describe the name of your module, what it requires to work, and which packages are visible outside this module.

For example, you can see what packages java.sql exports (makes visible) and which modules it requires.

jdbc:oracle:thin:@odbcoda-866-01.inmarsat.com:8200/SVWUAT1B

Moe about modules:
------------------
What is a module descriptor?
ans: 
A module must provide a module descriptor—metadata that specifies the module’s dependencies, the packages the module makes available to other modules, and more.

A module descriptor is the compiled version of a module declaration that’s defined in a file named module-info.java.

Each module declaration begins with the keyword module, followed by a unique module name and a module body enclosed in braces, as in:

module-info.java
---------------
module modulename { 
  ...
  ...
}



The module declaration’s body can be empty or may contain various module directives, including 
requires, 
exports, 
provides…with, 
uses and 
opens etc.


The keywords exports, module, open, opens, provides, requires, uses, with, as well as to and transitive, which we introduce later, are restricted keywords.

They’re keywords only in module declarations and may be used as identifiers anywhere else in your code.


requires:
---------
 A requires module directive specifies that this module depends on another module—this relationship is called a module dependency. 

 Each module must explicitly state its dependencies.

 When module A requires module B, module A is said to read module B and module B is read by module A.
 To specify a dependency on another module, use requires, as in:

requires modulename;

There is also a requires static directive to indicate that a module is required at compile time, but is optional at runtime. 


requires transitive—implied readability. 
----------------------------------------	
To specify a dependency on another module and to ensure that other modules reading your module also read that dependency—known as implied readability—use requires transitive, as in:

requires transitive modulename;


Consider the following directive from the java.desktop module declaration:

requires transitive java.xml; 

In this case, any module that reads java.desktop also implicitly reads java.xml.
For example, if a method from the java.desktop module returns a type from the java.xml module, code in modules that read java.desktop becomes dependent on java.xml.

So Without the requires transitive directive in java.desktop’s module declaration, such dependent modules will not compile unless they explicitly read java.xml.


According to JSR 379 Java SE’s standard modules must grant implied readability in all cases like the one described here. Also, though a Java SE standard module may depend on non-standard modules, it must not grant implied readability to them. This ensures that code depending only on Java SE standard modules is portable across Java SE implementations.


exports and exports…to. 
----------------------
An exports module directive specifies one of the module’s packages whose public types (and their nested public and protected types) should be accessible to code in all other modules.

An exports…to directive enables you to specify in a comma-separated list precisely which module’s or modules’ code can access the exported package—this is known as a qualified export.


uses.
-----
 A uses module directive specifies a service used by this module—making the module a service consumer.

 A service is an object of a class that implements the interface or extends the abstract class specified in the uses directive.


 provides…with.
 ---------------
  A provides…with module directive specifies that a module provides a service implementation—making the module a service provider.
 
  The provides part of the directive specifies an interface or abstract class listed in a module’s uses directive and the with part of the directive specifies the name of the service provider class that implements the interface or extends the abstract class.


  open, opens, and opens…to.
  --------------------------
   Before Java 9, reflection could be used to learn about all types in a package and all members of a type—even its private members—whether you wanted to allow this capability or not.

   Thus, nothing was truly encapsulated.

	A key motivation of the module system is strong encapsulation.

	By default, a type in a module is not accessible to other modules unless it’s a public type and you export its package.

	You expose only the packages you want to expose. With Java 9, this also applies to reflection.


    Allowing runtime-only access to a package. An opens module directive of the form

opens package
--------------
indicates that a specific package’s public types (and their nested public and protected types) are accessible to code in other modules at runtime only.
 Also, all the types in the specified package (and all of the types’ members) are accessible via reflection.

Allowing runtime-only access to a package by specific modules. An opens…to module directive of the form

opens package to comma-separated-list-of-modules
-------------------------------------------------
indicates that a specific package’s public types (and their nested public and protected types) are accessible to code in the listed modules at runtime only. All of the types in the specified package (and all of the types’ members) are accessible via reflection to code in the specified modules.

Allowing runtime-only access to all packages in a module. If all the packages in a given module should be accessible at runtime and via reflection to all other modules, you may open the entire module, as in:

open module modulename {
   // module directives
} 

Reflection Defaults
-------------------
By default, a module with runtime reflective access to a package can see the package’s public types (and their nested public and protected types). However, the code in other modules can access all types in the exposed package and all members within those types, including private members via setAccessible, as in earlier Java versions.

