---
layout: post
title: Modeling Method
---

A Modeling Method is a set of rules, guidelines and prescriptions for the creation of a model. 

A Modeling Method cannot be taken off the shelf. There are a lot of methods out there that are very good; and they will be a perfect starting point to create a Modeling Method for a specific company. 

The problem with the "standard" modeling methods (think UML or the UP) is that they are far too large and generic. You will never need all elements described in UML, but you probably will need several "types" of classes. 

If the users of the Modeling Method in some way react like this, it's an indication there might be room for improvement

> _So I was bound to work with a non-existing meta-model and bloated processes
> that were once designed for a different department and a stack of dozens of
> Word templates which had to be filled with useless words just for the sake 
> of being filled and once that happened they could report that we have 
> reached a new milestone_.

> Quoted from Jan "ebeb" on the Sparx Systems Enterprise Architect forum.

The Modeling Method should be tailored to the needs of the users and their specific needs. A Modeling Method is a tool, not a holy bible written in stone, it should adjust itself to the users, not the other way around. It should give the users the exact tools they need to best describe their domain in all aspects they require.

A "full" Modeling Method always contains three parts:

* Way of Thinking
* Way of Working
* Way of Writing

<canvas id="Modelling_Method_w" class="UmlCanvas"><span></span></canvas>

## Way of Thinking

The Way of Thinking or *Semantics* defines the concepts that are used in the Modeling Method. Each concept gets a formal and precise definition, and each of the relations is explained. For Modeling Methods that are based on an industry standard such as UML, a part of the definition is already provided by the UML elements that are being used. The other part will be specific to this modeling method. An industry standard such as UML provides very generic abstract concepts such as Class or Component. For a Modeling Method that is meant to be used in a concrete situation these concepts will need to be made concrete. Instead of a Class you could have a "Business Object", a "Controller" or a "Message". Each of these concepts could use the UML class, and comply with the description of a Class in the UML specification, but they still have their own very specific meaning, and are used in their own specific context.

## Way of Working

The Way of Working or *Process* describes the process part of the Modeling Method. Where to begin and how to go from one concept to another. It also describes the different steps in the analysis process, and which deliverables should be created at which point in the process. UML does not say anything about the Way of Working, it only describes the Way of Thinking and Way of Writing. An example of a method that describes the Way of Working is the UP. 

## Way of Writing

The Way of Writing or *Notation* describes how the model should be persisted. It discusses the graphical representation of the concepts, the structure of the model, naming conventions, and the CASE tool specific aspects of creating an analysis model.

# Documentation

A Modeling Method should be documented properly. A method without documentation is worthless because each user will quickly create its own version of the method in its head. This will inevitably quickly lead to inconsistent modeling results and local user-specific dialects, that will only be understood by the original author.

The statement that a Modeling Method should be documented may seem pretty obvious, but it is surprising how many companies create analysis models without some proper method documentation.

## Meta Model

The basis for the documentation is the Meta Model. This is in fact a model of the Modeling Method. Starting from the principle "eat your own dog food" the Meta Model should be modeled as much as possible using the exact same method it describes. This is not always possible since the modeling method is tailored to serve a specific purpose. A typical modeling method would be tailored to model administrative software models, business process model, etc... So it is not surprising that they are not entirely suitable to model Meta Models.

The diagram below shows an example of a part of a meta model.

<canvas id="Modelling_Method_m" class="UmlCanvas"><span></span></canvas>

The Meta Model describes the three parts of a Modeling Method: The Way of Thinking, the Way of Working and the Way of Writing. This means that we describe each modeling concept, describe the process of creating a model, and describe how this model should look like. All documents, websites, presentations, training guides etc. should be based on the Meta Model because this is the unique source for the Modeling Method. Preferably all documentation regarding the Modeling Method should be generated directly from the Meta Model. Do not make the mistake, as a lot of companies do, to create a lot of separate documents, websites, and presentations. All of these documents will quickly become a burden to maintain, slowing further developments of the Modeling Method.

## Documenting the Way of Thinking

The Way of Thinking describes the modeling concepts independent of the process in which they are created, or the way they are written down. So this part of the documentation should not contain any references to the CASE tool used or the development phase it is created in.
For each concept following topics should be described:

* Definition: Each concept gets a formal definition. This describes unambiguous, in clear words what the concept is. In this definition it is important to be as concrete as possible. Abstract vague descriptions are very good for consultants selling their product to a bunch of "pointy haired" managers, but they will not help the users. 
* Properties: Each concept can have some properties that are important to be recorded. Most concepts have at least a *Name* and a *Description*, but there could be a lot of other properties that we are interested in such as *Precondition*, *Multiplicity*, *Abstract*, etc... Each property should have proper documentation of its own with a definition and some examples.
* Relations: No modeling concept stands on its own, independent of other concepts. Each modeling concept is related to other concepts. These relationships are as important as the concepts themselves. Every relationship between two modeling concepts should get its own documentation including a formal definition and examples.
* Examples!: Analogues to the saying "A picture says more then a thousand words" we could say *An example says more then a thousand definitions*. This is a part that is often neglected, or completely ignored in a lot of method documentation. I cannot stress the importance of creating examples more. An example will give the users the insight they need to really understand fine details of the definition, and get a grasp of the more abstract qualities such as granularity.

## Documenting the Way of Working

The way of working is the behavioral side of a Meta Model. It can be documented using a *Process Model*. This process model should describe a sequence of actions to be performed by the different users. The key is to know *Who does What When and How*. Questions like "How should I start?" or "How should I find use cases" should be answered by the documentation of the Way of Working.

Another aspect of the process is to know when which concepts should be delivered, and to which degree of detail.

The Way of Working will typically contain following elements:

* Actor: A person involved in the modeling process, or more precisely the *Role* a person plays in the process. Examples of such roles are *Business Analyst*, *Client* or *Developer*. There is a many-to-many relation between the people involved in a modeling process and the roles. The role of *Functional Analyst* could be played by many people, and a specific person could be both *Developer* and *Functional Analyst*.
* Activity: Is something an *Actor* does somewhere in the modeling process. For each activity is is important to know the *Preconditions* and the *Postconditions*. The *Precondition* describes what should be ready before the activity can be started, where the *Postcondition* describes what the result of the activity should be. *Create Use Cases* could be an example of such an activity. The actor that executes this activity would be the *Functional Analyst*. The Precondition could be that the *Business Processes* should be defined and the Postcondition could be that the *Use Cases* are defined. The next activity could then be *Review Use Cases*, where the Precondition of course would be that the *Use Cases* have to be defined.
* Deliverable: Deliverables are the result of modeling activities, and the input for other activities in the process. Although the most important deliverable should be that a part of the model is created, sometimes documents are required as well. Documents are usually requested by less technical roles (Manager, Clients) who do not find their way in the model. If a document is required this should always be generated from the model using a *Document Generator* (see chapter Tools) to prevent inconsistencies between the documents and the model.

## Documenting the Way of Writing

The Way of Writing deals with how the model is persisted. Which tools are used, how the model is organized, how it should look like etc... Where the Way of Thinking and the Way of Working are rather conceptual aspects of the Modeling Method the Way of Writing provides very concrete guidelines and conventions. Here (and not in the other aspects) the concept of a *Diagram* is first defined. This may seem a bit odd to some people who think UML is described as a set of diagrams, but diagrams are only there for communication. Remove all diagrams from a model and you do should not loose a single character of information. The only thing you will loose is a convenient way of reading and writing the model. Do not however make the mistake that diagrams are not important; to the contrary! Diagrams are crucial to communicate your model to the stakeholders. Create messy diagrams and your message will not come through loud and clear, resulting in less funding or wrong implementation. 

For each diagram, modeling concept, relation or deliverable following topics are described:

* Location in the Model Tree: Most models have the form of a hierarchical tree. This means that every diagram, modeling object and relation has exactly one containing element and therefore  a unique location in the tree. For each element in the model we should define where exactly in this tree it should be placed. (i.e. what is the type of the containing parent element)
* Usage in Diagrams: Describe in which diagrams the concept or relation is used. Do not forget to mention with which purpose it is used on a specific diagram.
* Graphical Representation: Describe the guidelines regarding the graphical representation on the diagrams.
* Naming conventions: Most companies have some sort of naming convention. Naming conventions help the users to quickly see the concept type of a modeling object. Naming conventions usually include prefixes, postfixes or numbering.
* CASE Tool specific guidelines: Models are created in a CASE tool. For each concept we describe which element in the tool is used to represent it, and which fields in the tool we use to store the properties of the modeling object.
* Examples!: Again, examples are very important. Only examples give a real feeling of what the guidelines are trying to bring across.

## Types of Documentation

The documentation for the Modeling Method can take several forms, depending on the use of the documentation and the intended audience. Every piece of documentation should however be based on the same source, the Meta Model. It should ideally be generated directly from the Meta Model so that, in case a concept changes, all documentation is automatically updated. 

In general we can distinguish following types of documentation:

* Reference: The reference documentation is the full documentation with all the details. Every concept, every property and every constraint can be found in this reference. This really is the ultimate and complete source of all aspects of the method. This can be in the form of a document, but it is probably better provided as a website, or even as a model in the companies chosen CASE tool. The difficulty with using a document form is that it is linear, where the meta model is not. There is no beginning or end to a Modeling Method so any linear form would be somewhat awkward. The goal of the reference documentation is that users, when working on models, can check the prescriptions and guidelines of the method. This type of use is easiest when you can search the documentation to find the element or part that you are interested in, and then click-through to the related sections. 
* Cheat Sheet: A Cheat Sheet is a small document that contains only the most important elements of the meta model. It is used as a sheet that is always next to the modeler when he is working on his model to quickly see whether he is on the right track. The Cheat Sheet is not complete, and it is not meant to be. It provides the users with a quick overview of the most important concepts and their relations, and maybe a one sentence definition.
* Learning Book: The learning book provides a step-by-step path through the Modeling Method. It is used by new users who want to learn the method. After studying the learning book they should be capable to start working as a modeler in a team. Each subject should therefore be explained in enough detail. The difficulty for a learning book is to find a good path through the method. The process model of the Way of Working could be a good starting point.
* Training Slides: The training slides are the slides that are shown during an training course on the method with a teacher. These slides should not contain any verbose definitions, but highlight the different topics in the course with bullet points and illustrations. The slides can be given to the student to use as a memory aid. A student will probably remember in which part of the course a certain topic was discussed. He can then review the slides of the training to trigger his memory.
* E2E Example: In all the types of documentation examples are crucial to the understanding of the method. Without example the method will stay dry theory that will be interpreted in lots of different ways. You can create a new example each time it is required, but it will be a lot better to use one end-to-end example that covers all aspects of the method. Not only can this E2E example be the source for all examples in the different types of documentation, but it will be a source of information on its own. It allows a user to look at the example and find out how exactly a good model should be built. The subject of the example should be something that every body can easily understand, preferably in the domain of the users. If the method is designed for a bank then the E2E example should be an example within the financial domain. It does not have to be a "real" model, but the closer to the reality the better. Creating such an E2E example should not be underestimated. This is a very difficult task. First of all finding a good subject that covers as much as possible all scenario's, and secondly creating a model that conforms to every rule of the method is far from trivial
