---
layout: post
title: Modeling Tooling
---
As modelers we need tools to express ourselves. The most basic tool would be a pen and a piece of paper, but in a somewhat professional environment a modeler needs a decent CASE Tool. Next to this main tool there are a lot of other tools that are sometimes already provided by the CASE Tool, but in most cases these are custom developed by the company that uses the Modeling Method. The CASE Tool itself will not be discussed here, it deserves a separate page with reviews and evaluations of the different brands (see CASE Tool). In this section we discuss the custom made enhancements that work together with the CASE Tool and are most commonly found in companies that use a lot of modeling.

## Tooling Framework

The Tooling Framework is not a tool on itself but, as the name says, a framework to build tools on. The Tooling Framework is entirely based on the Meta Model. Every function is to be executed against the objects defined in this Meta Model as this is the language we think in. We define rules and behavior on meta objects, not on UML elements or even worse, on the elements defined in the CASE Tool's API.

The Tooling Framework is something that is often overlooked when a company starts to extend the functionality of their favorite CASE Tool. Most tools start as a quickly hacked together script to solve an immediate problem, but then get used more general, and before you know it they become an essential part of the companies operations. What usually happens next is that they discover that this "quick and dirty" tool is no longer maintainable, and a lot of money is spent on rewriting the whole lot. Even worse it is when the company wants to change to another CASE Tool. They find themselves completely painted in a corner, with no other choice than A. stay with the current CASE Tool or B. Start over completely with a complete new set of tools.

Actually there is no reason to think that tooling software is any different from the usual business software a company develops. If there is no analysis, no documentation, and a "quick and dirty" hacked together solution it will cost more in the long run.
The Tooling Framework provides a long term solution as it provides a loose coupling between the meta objects, the underlying modeling language, and the CASE Tool used.
The pattern to use for the Tooling Framework can be found here: Pattern:Modeling Tooling Framework

## Model Validation

In the industry there is quite a lot of discussion about what Model Validation really means. 

Some sources make a difference between *Validation*, in the sense of validating that the product meets the user requirements, and *Verification* in the sense of verifying that the model complies to the established rules of the Modeling Method.

Most CASE tool vendors describe the latter as Model Validation.

In this article we have followed the CASE tool vendors.

The Model Validation Tool is an essential part of the process of you want to ensure the quality of the model. 

This tool will validate (a part of) the model against all rules defined in the Modeling Method. Some CASE Tools such as Mega have a built-in facility to validate models. But even in that tool you still have to write out the rules using their own custom scripting language. You can wonder whether, if you still have to program the rules, it is worth using the built-in facility, especially because this increases the vendor lock-in and makes it harder to switch to another brand. And of course, the built-in facility only knows about the concepts of the tool, not the concepts used in the Modeling Method

No, then you can better use the Tooling Framework, the provided objects are the exact concepts used in the method, which is also the level you want to define the rules on. You don't think about rules in terms of classes or operations, but you think in terms of *component facades* or *system services*.

All rules to be validated are directly derived from the Meta Model. Think about which relations with other meta objects are allowed or required, which attributes should be filled in, or how the model should be structured. In general validation rules can be divided into 4 categories

* Fields
* Relations
* Naming Conventions
* Diagrams

The primary user of the Model Validation Tool should be the modeler. It should become a habit to validate a part of the model before committing it, just like a developer will always compile (and hopefully test) his code before he commits it. Because of this intended use the Model Validation Tool should be easy to use. If a modeler just finished a part of the model he wishes to quickly run the validation, and then easily fix all the reported errors. This brings us to the following list of requirements.

* Quick: If it is going to take more than about a minute to run the validation then the modeler probably isn't going to bother. He certainly will not keep running the validation until all errors are fixed.
* Precise: If the modeler just finished a specific part of the model he only wishes to see the errors on that specific part of the model. If the tool is going to report every single error in the whole model it is going to be difficult to filter out just that part that was worked on. You could even think about limiting the validation to elements that are changed in a specific time frame. This will however not help in fixing errors that were there already before the modeler began his work on that part.
* Easy to fix: The result of the validation should be a list of errors stating the object where the error was found, which rule was violated and what the user should do to fix it. Next to those there should be a one-click possibility to open the offending object in order to fix the error.
* No false positives: This is similar to the boy who cried wolf. If the validation reports errors that are actually correct implementations then the real errors will be lost in the heap. It will be hard for the users to distinguish the real error from the false positives, resulting in errors that stay in the model. This is harder then you would think. There are all kinds of rules that apply to "most" of the cases or "almost" all objects. These types of rules should be avoided at any time. If you cannot make a black and white decision on whether something is correct or not then it shouldn't be a rule in the validation tool.
* Allow exceptions: No matter how we try to avoid the false positives there will always be exceptions. The tool should allow some mechanism to indicate that a specific object is an exception, so that it doesn't come up in the error list next time the validation is run. This will allow us to demand an error free model before committing.

## Document Generator

Another tool that almost any company that does modeling uses is the Document Generator. This tool is used to extract human readable document from the model. These documents are usually the deliverables in the development process, they are used to discuss the requirements with the client, agree on the the architecture with the architecture team, present the global solution to the management, etc.

Having a Document Generator in such circumstances is absolutely critical. Without a good document generator the users will have to copy/paste each element from the model into the document. Now when this carefully copy/pasted document is discussed, and some changes need to be done, then the temptation to just quickly change the document, without changing the model will be great. After all, we are all under pressure to deliver on time and under budget. Without proper supervision this will quickly lead to a situation where only the diagrams are still created in the model. All other documentation will then only be created in the delivery documents, and if necessary copy/pasted into other documents. This degrades the CASE Tool to nothing more then an expensive version of [Visio](http://office.microsoft.com/visio), and leaves the maintenance team without any structured system documentation.

This document could be something in the form of a Rich Text Format, MS Word or other similar formats. A document is typically structured in a linear way. There is a beginning and an end, and if you have read the document from the beginning to the end you have seen everything. This is in contrary to the structure of a model. There is no beginning and end, and certainly not a path that can be followed to read everything. It is this discrepancy between the nature of a model and the nature of a document that makes it difficult to create good, readable and complete documents based on the model.

The need to create documents is so general that almost every CASE Tool has some sort of facility to generate documents. With these built-in generators you can create documents that are fine at the first glance, but not perfect. The fact that the demonstration documents look nice will persuade a lot of companies to try using this built-in generator. But after a while most of them get disappointed and frustrated because they cannot get exactly what they want. The thing is that those generators usually do one pass over the whole or part of the model, which means that the document has to follow the hierarchical structure of the model where the documents that the user wants to create usually does not follow this hierarchy. In the end most companies figure out that trying to create decent documents with the built-in document generator is very costly and not providing them exactly what they require. Only after this painful experience they are willing to invest in a custom built Document Generator.

Again the Document Generator should be based on the Tooling Framework. The requirements for a certain document template will be expressed in terms of the concepts of the Meta Model. They might say something like: _From a business process show the "business context diagram" and the "business process content diagram". Then list the realizing "system use cases" with all the scenarios_ With the Tooling Framework these type of requirements can be translated directly into the template definition, without the need to use large switch/case statements to figure out which type of element you are dealing with.

The main requirements for a good Document Generator are:

* Easy and Quick: Generating an average document (~50 pages) should not take much more then a minute. Remember if generating a document is much slower then just editing the document then the latter will inevitably happen.
* Perfect: The generated document has to be ready to use. It should not look like a generated document. So no white space, no unnecessary technical terms are allowed. This is most important for documents that will be used to communicate with clients or management. In general clients and managers will be completely turned off by documents that look anything like something technical. There is a good chance they will not even read it. Therefore a generated document has to look like it was hand crafted.  If a user first needs to spend half an hour fidgeting with the layout of the generated document then he will surely not want to do it a second time, and he will be tempted to edit the document directly.
* Regenerable: It should be very easy to regenerate a part or the whole document. This is again to avoid the manual editing of the document by the overworked user who doesn't have the time now to regenerate the whole document.

## Model Templates

The Model Templates is another type of tool that almost any company that does modeling has in some form. This tool allows you to create a certain standard part of the model, a part that has a specific structure and follows the naming conventions of the modeling method.
This part of the model could be for example a *system component* with its provided *system interface* and a *system component dependencies* component diagram.

If the users have to create all the elements of such a structure manually there is a good chance they will forget something, or make a mistake in the structure or naming convention. The Model Templates tool helps them save time, and avoid those "syntax" type of errors.

This tool should again be based on Tooling Framework. The specific logic of the tool would then be very limited and would basically perform following steps:

* The users selects a location in the model to create a part
* The tool presents the user with the allowed options for that location. Using the Tooling Framework this will be a trivial task as the tool would only need to ask that question to the framework.
* User selects the type of structure to create.
* User enters a name for the new structure.
* The tool gets the details for the structure and creates the elements into the CASE Tool.

Using the Tooling Framework will ensure that the newly created part is compliant with the Modeling Method.

The definition of the templates could also take many forms. It could be hard coded in the tool, based on some sort of template definition file (think XML) or it could even point to a specific part of the model. This last option is probably the easiest way to define the templates as parts of the model itself can be copied and used as a template.

## Productivity Enhancements

The Productivity Enhancements are actually a collection of (small) tools to help the user when modeling. These are the kind of small things that are not required, but are there to make the life of the users easier, and of course more productive. The Model Templates Tool could also be considered as a Productivity Enhancement, but is discussed separately because this tool is used in most modeling teams, and is a bit larger then most of the Productivity Enhancements discussed in this section.

Usually these are realized as add-ins on the CASE Tool. Think about tools to

* Navigate from one element to another (like get *System Collaboration* for *System Interface Operation*)
* Fill in a documentation template for a specific Meta Model instance
* Copy a part of the model

Most of these little add-ins also benefit from the Tooling Framework for the same reasons as all the other tools. Even if the advantage of using the Tooling Framework is not immediately clear you might want to consider to use it anyway to remain consistent with the other tools.
