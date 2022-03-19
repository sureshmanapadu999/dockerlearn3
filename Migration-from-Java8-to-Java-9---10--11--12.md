Parts of the Java Platform Module System are designed to ease migration of applications written in pre Java 9 to Java 9. The module system is designed to support "bottom up migration" - meaning that you migrate your small utility libraries first, and your main applications last.

The migration is intended to go something like this:

Upgrade to Java 9, and run your application without modularizing anything. 
Put classes and JAR files on the classpath as normal. These classes then become part of the unnamed module. 

Move utility library JAR files to the module path. This way they become automatic modules. Do this for both internal and third party utility libraries. The main applications should still be on the classpath in the unnamed module. The unnamed module can read all named modules, automatic or non-automatic. 

Migrate internal and third party utility libraries to Java modules when possible. Place the Java modules on the module path. Start with libraries that have no other module / JAR dependencies, and move up in the dependency hierarchy. 

Migrate your main applications to Java modules.

By upgrading bottom up the chance is higher of your applications being able to work in the period before everything is upgraded to Java modules. Your application is supposed to be able to work during any of the above phases.

Upgrading utility libraries first to automatic modules, and later to full modules, starting at the bottom of the dependency hierarchy, should assure that your libraries can still read each other during upgrade, plus be readable by the main applications on the classpath in the unnamed module.

Note: If there is any chance of you upgrading everything in one big upgrade, that will most likely be the easiest upgrade path. Of course you will have some time where you may not be able to assemble a working application, but once you are through it, you are through it! You are not dragging old dependencies around in your application. If possible, this is definitely preferable.