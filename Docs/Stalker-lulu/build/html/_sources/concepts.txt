Stalker Concepts
================

Stalker Object Model
....................
* **Studio** :

With Stalker you can manage all you Studio data by using this class. 
Studio knows all the projects, all the departments, all the users and every thing about the studio. 
But the most important part of the Studio is that it can schedule all the Projects by using TaskJuggler.

* **Project** :

An animation/vfx studios duty is to complete a Project .
A project, generally is about to create a Sequence of Shots which are a series of images those at the end converts to a movie. 
So a sequence in general contains Shots. 
And Shots can use Assets. 
So basically to complete a project the studio should complete the shots and assets needed by those shots.
Project is one of the main classes that will direct the others. A project in Stalker is a gathering point.

* **Sequence** : 

Sequences are a way of grouping the Shots according to their temporal position to each other.

* **Shot** : 

Manages Shot related data.

* **Asset** :

Assets are containers of Tasks.And Tasks are the smallest meaningful part that should be accomplished to complete the Project.
These Tasks can be defined by the type of the Asset, which is a Type object created specifically for Asset .
So basically to complete a project the studio should complete the shots and assets needed by those shots.

* **Task** :

Furthermore all the Projects, Sequences, Shots or Assets are divided in to different Tasks those need to be done sequentially or in parallel to complete that project.
Tasks are the smallest unit of work that should be accomplished to complete a Project.
Tasks define a certain amount of time needed to be spent for a purpose. 
A Task relates to a work, a work is a quantity of time spent or going to be spend for that specific task. 

* **TimeLog** :

Holds information about the uninterrupted time spent on a specific Task by a specific User.
A Task relates to a work, a work is a quantity of time spent or going to be spend for that specific task.
The time spent on the course of completion of a Task can be recorded with TimeLogs. 
TimeLogs show the total time spent by an artist for a certain Task. 
So it holds information about how much effort has been spent to complete a Task.

* **Repository** :

A repository is a network share that all users have access to.
During the completion of the Task or at the end of the work a User creates Versions for that particular Task.
Versions are the different incarnations or the progress of the resultant product, 
and it is connected to files in the fileserver or in Stalkers term the Repository.


To create a Project, we need:
.............................

* A Repository
* A Structure object to define the file structure of the Project:
* FilenameTemplates for Task, Asset, Shot, Sequence types, to define the placement of the Versions created for them.
* An ImageFormat to define the output size of the project.
* A StatusList with enough Statuses that will define the desired Project Statuses. Stalker doesn’t have a Project Status Workflow, yet! so define yours.
* If desired we can also add a Type for the Project to distinguish commercials from Feature Film projects.
* We need to create a user as the lead for the project.