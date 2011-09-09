---
layout: post
title: Abstract Factory
---
The *Abstract Factory* pattern provides an easy way to create objects that belong to a specific family without the need to keep a hard coded reference to their classes. The client application only needs to know the abstract product definitions, without worrying about the different implementations. 
Using this pattern make it easy to create a whole new family of products without changing anything to the client.

The *Client* class in this pattern only knows about abstract *ProductA* and  and the abstract *ProductFactory*. Whenever it needs a new *ProductA* it will call the operation CreateProductA() on the *ProductFactory*. Depending on whether the instance of the *ProductFactory* is actually a *Family1Factory* or a *Family2Factory* the client will receive a *ProductA1* or a *ProductA2*.

Adding a new family of products, say *Family3*, is very easy, and does not have any impact on the client. All that needs to be done is to create a new subclass of the *ProductFactory*: *Family3Factory* and a new subclass of the *ProductA*: *ProductA3*.

Adding a new product, say *ProductB* is much less trivial as it requires addition of an operation CreateProductB() on the ProductFactory, and each of its subclasses. Additionally there will need to be a new abstract *ProductB*, and a subclass of *ProductB* for each of the product families. And of course, the *Client* will need to be adapted to use this new *ProductB*

##  Area of Applicability 

### When to use

* When an application will need to work with a limited set of products that can have various "family like" implementations.
* The application needs to be independent of the implementation of the products.

### When not to use

* When the set of products is not stable.

##  Example of Usage 
This example shows a design for a report generator. The generator is able to create reports targeted at different technologies, in this case HTML, PDF or Excel. Each report will contain a header and a body. 

Since the used technology does not influence the logic in the *ReportGenerator* we do not want this class to be polluted with details regarding the targeted technology. Therefore the ReportGenerator only knows about the abstract classes *ReportHeader* and *ReportBody*. This *ReportHeader* and *ReportBody* are the _Products_ in the pattern.

In order to create the parts of the report the *ReportGenerator* will call the *ReportFactory*. An instance of the factory *HTMLFactory*, *PDFFactory* or *ExcelFactory* will be passed to the *ReportGenerator* depending on the choice the user has made. The *ReportGenerator* however does not need to be aware of these different subclasses of the *ReportFactory*. 

HTML, PDF and Excel represent the different _Families_ in the pattern.

<canvas id="Abstract_Factory_m" class="UmlCanvas"><span></span></canvas>

We could very easily imagine a dozen other technologies that a report can be created in. Adding such a technology to this design will be a breeze. All you need to to is create a new subclass of *ReportFactory*,*ReportHeader* and *ReportBody*, and make sure the new *ReportFactory* is passed to the *ReportGenerator*.

Adding a new product, say a *ReportFooter*, on the other hand is much more trouble. Each of the factories will need to implement a new operation to create the footer, and this new *ReportFooter* will need to be implemented in each of the existing technologies.

##  Integration

This integration example shows how to combine the *Abstract Factory Pattern* with the Adapter Pattern. These two patterns go exceptionally well together. It was even difficult to find a good example of *Abstract Factory* that didn't include Adapters.

The example features an application to import an ADL model into a CASE tool such as Enterprise Architect or Rational Software Architect.

ADL or Abstract Domain Language is an abstract condense language to describe elements in a domain. It is used by UmlCanvas to describe a UML diagram to display on a web page.

Most CASE tools provide some kind of API to connect to the model from within another application.

Usually this API contains classes such as "Class", "UseCase", "Operation" etc... These classes can then be used to manipulate the model in the CASE tool. They each have their specific way to create a class, create a use-case, add an attribute to a class, add an operation to a class etc...

<canvas id="Abstract_Factory_eou" class="UmlCanvas"><span></span></canvas>

Of course you do not want your main business logic to be dependent on the specific implementation of the CASE tools API. Instead you create your own representation of the model. The abstract classes *Class* and *UseCase* represent the concepts of Class and UseCase in a tool independent way. These classes contain operations to manipulate and query them.

Next you create a subclass of these independent classes for each family i.e. an *AEClass* and a *RSAClass*; an *AEUseCase* and a *RSAUseCase*. These tool specific classes know how to use the classes provided by the CASE Tool API. They are the wrappers or Adapter classes for the classes provided by the API.

To create a *Class* or *UseCase* the *ADLImporter* calls the appropriate operation on the *CaseToolFactory*. Depending on the specific subclass of the *CaseToolFactory* that is instantiated, the ADLImporter will receive objects from the RSA family or the EA family.

More about extending a CASE Tool can be can be found in the Modeling Tooling Framework Pattern

##  References 
Design Patterns: Elements of Reusable Object-Oriented Software

##  See Also 
* Factory Method 
* Prototype 
* Singleton
* Adapter


