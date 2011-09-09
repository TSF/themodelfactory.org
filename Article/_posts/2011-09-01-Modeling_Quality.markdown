---
layout: post
title: Modeling Quality
---

Before we discuss what quality in an analysis model is we should look a the different goals of such a model. A good model will allow to

* Discuss the requirements with the stakeholders: The model is used to agree about the requirements with the stakeholders to make sure that the software that will be developed is exactly what is requested by the client. This will result in less change requests and a greater user satisfaction.
* Provide a handover deliverable to development: Another goal of the model is to provide the exact specifications of what has to be built by the development team. This means that the requirements agreed with the business have to be translated into a software design that can be built by development. Failing to provide this will inevitably lead to more software bugs.
* Be used as system documentation: Once the system has been build and delivered it has to be maintained. A good model can be used as system documentation, allowing to quickly and exactly locate the part that needs to be changed, or perform impact analysis when something needs to be changed. 

## Characteristics

Following are the characteristics of a high quality analysis model.

* Consistent: A good model describes thing everywhere in the same way. This means that there cannot be local "dialects", and one should not be able to tell the author just by looking at a part of the model. When a model is consistent it becomes easy for a user to switch from one part to the other without the need to familiarize himself with the (dialect of the) method used in that part of the model. Consistency in a model will require less "intake" time, will increase the overall understanding, and will decrease misunderstandings and the resulting change requests or bugs.
* Complete (breadth): A good model describes the subject completely. There should be no blind spots or parts of the subject that are not described. If the model is complete a user should not have to wonder whether there might be a part of the subject that was not documented. Only a complete model can effectively be used as system documentation. If for some reason it is not possible to describe the subject completely then the missing parts should at least be recognized and listed.
* Precise (depth): A good model should describe the subject with enough detail. Every aspect that is relevant for the development of the system should be documented. The model should be usable as a complete specification by the developer. If the developer has to ask the analyst all kinds of questions about details in the model this means that is was not documented in enough detail. Determining the exact level of detail required is always a difficult question. Some companies are already happy when the main classes are defined, where other require that every operations is documented with extensive pseudo code or sequence diagrams. This doesn't mean the analyst and developer should not communicate; to the contrary. Verbal communication is very important to ensure a good handover, but it should be backed up by a model that reflects everything that is communicated verbally.
* Unambiguous: A good model should never be vague. Every piece of information in the model should very clearly, without a doubt, mean what it means. If there is ambiguity in the model it will be understood differently by different users. The business may think the description means A where the analyst meant to say B, and the developer might create C. This is better explained by the cartoon below from [http://www.businessballs.com](http://www.businessballs.com).

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing1.png](images/Treeswing1.png)<br>
what marketing suggested
</div>

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing2.png](images/Treeswing2.png)<br>
what management approved
</div>

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing3.png](images/Treeswing3.png)<br>
as designed by engineering
</div>

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing4.png](images/Treeswing4.png)<br>
what was manufactured
</div>

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing5.png](images/Treeswing5.png)<br>
as maintenance installed it
</div>

<div class="illustration" style="width:300px;height:300px" markdown="true">
![Article/images/Treeswing6.png](images/Treeswing6.png)<br>
what the customer wanted
</div>

<br clear="both">

* Genuine: A good model represents the objective reality of the subject. Again this might seem obvious as a statement, but it is far from obvious to achieve. Because every person sees things in a slightly different way it is very difficult to come to an objective representation that isn't colored by the way the modeler tends to see things. Although the model should be objective that doesn't mean that there is only one way to correctly represent a subject. There can be more then one way to represent something, though one specific model might be considered better then another one. Judging this aspect cannot be put into formal rules and is therefore very difficult. It can only be judged based on experience and knowledge of the subject.

# Quality Assurance

The Meta Model is the basis of Quality Assurance. Without a properly documented Meta Model you cannot hope to increase the quality of the model. We can only try to improve things once we know what a good model should look like. There are two way to handle QA: Preventive and Reactive. Both approaches should be applied in parallel to effectively increase the quality of the models.

## Preventive

* Training: New employees that are not familiar with the method have to be trained. The most effective type of training is an interactive course given by the experts on the matter. Next to the theory there should also be enough time to do hands-on exercises that make the often abstract theory more concrete. A good training course should not take much longer than a week. After this week the students should be allowed to put their new knowledge into practice. This first week might not be enough to learn every little detail of all parts of the method, but it should be enough for a basic course. Later advanced courses can then be used to explore certain subjects in more detail. If a course lasts more than a week then student will begin forgetting the details of the subjects treated in the first days.
Training is mostly focussed on new users that are not familiar with the method yet, but also experienced users can benefit from regular thematic sessions that explore a specific part of the Modeling Method in more detail. Especially those parts where a lot of errors where found during the reviews will be good candidates to be subject for the "refresh" sessions.
* Coaching: Providing only training for the users is not enough. A training session will only provide the users with the initial knowledge of the method. A training can never teach every rule or habit within a company, it only gives the users a strong basis to start with. When they are actually modeling is when the questions arise. They start to wonder whether they should model something this way, or the other. This is the moment that the coach needs to provide the necessary guidance. Not necessarily because one way is better then the other, but because one way is the way it is done in the Modeling Method.
Ideally there should be a coach available for every team of about 10 users. This coach should always be readily available when the users have some kind of question during modeling. If they first need to pick up the phone, or make an appointment with the coach, they will not bother and just make a (possibly wrong) choice. Being a modeling coach should not be a full-time job either. It should be something a senior modeler does next to his regular modeling tasks. This is to avoid the *ivory tower syndrome* of the methodologists. When somebody has only coached other people for a few years he will inevitably loose contact with the "floor". He will only know how things should be in theory but forget the everyday issues the modelers face.
* Tooling: Tooling can also be a great aid in the prevention of modeling errors. Configuring the CASE tool such that it really helps the users is the first step. Think about configuring the allowed types of attributes, allowed stereotypes, etc... When the CASE tool is properly configured you could also think about customizing the tool in such a way that it helps the user when modeling. If you for example require components to follow a certain naming convention, and have a specific structure, then a tool that creates a new component, complete with naming conventions and structure could be a great help. It avoids the most common typo's and users errors. More about tooling in the section Tools

## Reactive

* Model Validation Tool
  A Model Validation Tool checks the "syntax" type of errors in a model. The most important goal of the tool is to provide a modeler the possibility to check the part that he just created for errors before submitting. The Model Validation Tool should also be used as a part of the development process. A model that is delivered to the next stage in development should at least pass the Model Validation Tool. The tool can also be used to measure (an aspect of) the quality of the whole model and show the overall progress in improving the quality in the model. For more details on the tooling aspects see Model Validation.
* Model Reviews
  On a regular basis parts of the model should be reviewed by the QA specialist. Not to focus on "syntax" because that is already covered by the Model Validation Tool, but to check the other, less tangible, quality aspects of the model (precision, completeness,...).  Because this is a manual job it will not be cost-effective to review every part of the model that is delivered. Instead random deliverables can be reviewed. The results of the review should be discussed with the author of that part of the model, but general trends should be discussed with all users to focus their attention to these common errors or bad habits.
