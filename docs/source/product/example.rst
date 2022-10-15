=========
Example
=========


UML Diagram
=================

UML diagram can be written in PlantUML style. Comprehensive document can be found at https://plantuml.com/.


Component Diagram
------------------

.. uml::

  @startuml
  title sample component diagram
  package Server {
    node instance
    node gateway
    instance -- gateway
  }
  package Local {
    node PC {
      node Browser
    }
  }
  Browser -u- gateway
  
  @enduml


Activity Diagram
------------------

.. uml::
  
  @startuml
  title sample activity diagram
  start
  :write document;
  if (any update exists?) then (yes)
  :commit;
  else (no)
  :do nothing;
  endif
  :push;
  end
  @enduml

Gantt Diagram
-------------------

.. uml::
  
  @startuml
  title sample gantt diagram
  Project starts 2022-10-10
  2022/10/14 is colored in salmon
  [setup repo] starts 2022-10-15 and lasts 5 days

  then [write docs] lasts 10 days
  note bottom
  note for write docs
  end note

  then [publish docs] lasts 10 days
  @enduml
