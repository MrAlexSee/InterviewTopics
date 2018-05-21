General
--------------------

### Data structures

##### Basic

BST is assumed to be balanced.
Average case for hash table, worst-case is `O(n)`.

Structure  | Access     | Search     | Insert/delete  | Space
---------- | ---------- | ---------- | -------------- | -------
Array      | `O(1)`     | `O(n)`     | `O(n)`     | `O(n)`
List       | `O(n)`     | `O(n)`     | `O(1)`     | `O(n)`
BST        | `O(log n)` | `O(log n)` | `O(log n)` | `O(n)`
Hash table | `O(1)`*    | `O(1)`     | `O(1)`     | `O(n)`

* [Suffix tree](https://en.wikipedia.org/wiki/Suffix_tree):

* [Suffix array](https://en.wikipedia.org/wiki/Suffix_array):

### Algorithms

##### Graphs

* [A*](https://en.wikipedia.org/wiki/A*_search_algorithm): pathfinding,

* [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm): specific case of A* without a heuristic

##### Trees

* [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm): minimum spanning tree.

###### Pathfinding


##### String matching

###### Online

###### Indexed


### Design patterns

##### Creational

The summary is based on [Wiki](https://en.wikipedia.org/wiki/Software_design_pattern).

* Abstract factory:

* Builder:

* Dependency injection:

* Factory:

* Lazy initialization:

* Multiton:

* Object pool:

* Prototype:

* RAII: constructor/destructor:

* Singleton:

##### Structural

* Adapter:

* Bridge:

* Composite:

* Decorator:

* Extension:

* Facade:

* Flyweight:

* Front controller:

* Marker:

* Module:

* Proxy:

* Twin:

##### Behavioral

* Blackboard:

* Chain of responsibility:

* Command:

* Interpreter:

* Iterator:

* Mediator:

* Memento:

* Null object:

* Observer:

* Servant:

* Specification:

* State:

* Strategy:

* Template method:

* Visitor

### Architectural patterns

* Blackboard

* MVC:

* MVP:

* MVVM:

### Principles

* [Broken windows](https://en.wikipedia.org/wiki/Broken_windows_theory):

* [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself): avoid redundancy

* [KISS](https://en.wikipedia.org/wiki/KISS_principle): keep it simple, stupid

* [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method): project planning: must have, should have, could have, won't have

* [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization): constructor/destructor

* [SOLID](https://en.wikipedia.org/wiki/SOLID):

* [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better):

* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it): don't add functionality until necessary

### Project planning

C++
--------------------

##### C++11

###### Lambdas

###### Multithreading

###### Smart pointers

##### C++14/17


Python
--------------------

### List comprehension

Git
--------------------

Basic commands:

* `git clone [address]`

[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration): merging all working copies several times a day in order to mitigate integration problems.

[Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery): short cycles, software can be released at short notice.

### GitFlow

[GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow): workflow model based on branches.

* **master** branch: releases with version numbers
* **develop** branch: integration branch for features

* feature: branched out of and into develop, single feature = single branch
* release: branched out of develop, no new features can be added, merged into master when ready to ship, also merged back into develop