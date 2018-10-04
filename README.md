Table of Contents
--------------------

1. [Table of Contents](#table-of-contents)
1. [General](#general)
    * [Basic math](#basic-math)
    * [Complexity](#complexity)
    * [Graphs](#graphs)
    * [Data structures](#data-structures)
        * [Basic](#basic)
            * [Binary search tree](#binary-search-tree)
            * [Heap](#heap)
        * [String matching](#string-matching)
    * [Algorithms](#algorithms)
        * [Graphs](#graphs-1)
        * [Machine learning](#machine-learning)
        * [Sorting](#sorting)
        * [String matching](#string-matching-1)
            * [Exact](#exact)
            * [Approximate](#approximate)
        * [Trees](#trees)
    * [Design patterns](#design-patterns)
        * [Creational](#creational)
        * [Structural](#structural)
        * [Behavioral](#behavioral)
    * [Architectural patterns](#architectural-patterns)
        * [MVC](#mvc)
        * [MVP](#mvp)
        * [MVVM](#mvvm)
    * [Language-related concepts](#language-related-concepts)
        * [Object-oriented terminology](#object-oriented-terminology)
    * [Principles and abbreviations](#principles-and-abbreviations)
    * [Project planning](#project-planning)
        * [Things to consider](#things-to-consider)
        * [Scrum](#scrum)
    * [Testing](#testing)
        * [Unit testing in C++](#unit-testing-in-c)
    * [Useful Linux commands](#useful-linux-commands)
        * [General](#general-1)
        * [Compression](#compression)
        * [Conversions](#conversions)
        * [Net](#net)
        * [Packages](#packages)
1. [C++](#c)
    * [Basic](#basic-1)
        * [Bitwise operators](#bitwise-operators)
        * [Casting](#casting)
        * [Data parsing](#data-parsing)
        * [Memory management](#memory-management)
        * [Namespaces](#namespaces)
        * [Operator overloading](#operator-overloading)
        * [Preprocessor directives](#preprocessor-directives)
        * [Program segments](#program-segments)
        * [Templates](#templates)
            * [Template specialization](#template-specialization)
            * [Template metaprogramming](#template-metaprogramming)
        * [Time measurement](#time-measurement)
        * [Variadic functions](#variadic-functions)
    * [Standard Library](#standard-library)
        * [Map](#map)
        * [Set](#set)
        * [String](#string)
        * [Vector](#vector)
    * [C++11](#c11)
        * [Array](#array)
        * [Functors](#functors)
        * [Initialization](#initialization)
        * [Lambdas](#lambdas)
        * [Move semantics](#move-semantics)
        * [Multithreading](#multithreading)
        * [Range-based for loop](#range-based-for-loop)
        * [Smart pointers](#smart-pointers)
        * [Tuple](#tuple)
        * [Using](#using)
    * [C++14](#c14)
        * [Chrono literals](#chrono-literals)
        * [Deduced return type](#deduced-return-type)
        * [Improved lambdas](#improved-lambdas)
        * [Variable templates](#variable-templates)
    * [C++17](#c17)
        * [Filesystem](#filesystem)
        * [Folding for parameter packs](#folding-for-parameter-packs)
        * [Nested namespaces](#nested-namespaces)
        * [Optional](#optional)
        * [Unpacking tuples](#unpacking-tuples)
    * [Makefile](#makefile)
1. [Python](#python)
    * [Selected features](#selected-features)
    * [Functions](#functions)
        * [Running main](#running-main)
        * [Calling with args](#calling-with-args)
        * [Keyword args](#keyword-args)
    * [Classes](#classes)
        * [Inheritance](#inheritance)
    * [File system](#file-system)
    * [Filter, map, reduce](#filter-map-reduce)
    * [List functions](#list-functions)
    * [Multithreading](#multithreading-1)
    * [Plotting](#plotting)
    * [Time measurement](#time-measurement-1)
1. [Git](#git)
    * [Basic commands](#basic-commands)
    * [Related terminology](#related-terminology)
    * [GitFlow](#gitflow)
1. [Acknowledgements](#acknowledgements)


General
--------------------

### Basic math

* [Arithmetic series](https://en.wikipedia.org/wiki/Arithmetic_progression) sum: n(a1 + an) / 2 = ϴ(n²)

* [Bayes theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem): P(A|B) = P(B|A) P(A) / P(B)

* [Binomial coefficient](https://en.wikipedia.org/wiki/Binomial_coefficient) (number of ways to select unordered items): n! / [k! (n - k)!], for ordered items: n! / (n - k)!

* [Harmonic series](https://en.wikipedia.org/wiki/Harmonic_series_(mathematics)) sum: 1 + 1/2 + 1/3 + ... + 1/n = ln n + O(1)

* There are n! [permutations](https://en.wikipedia.org/wiki/Permutation) for n elements: n ways to choose the 1st element, n-1 ways to choose the 2nd element, etc. k-permutation = permutation of subsequence of length k.


### Complexity

* o() binds from above >, O() binds from above ≥, ϴ() binds from above and below, Ω() binds from below ≤, ω() binds from below <
* O(1) < O(log n) < O(n) < O(n log n) < O(n<sup>2</sup>) < O(2<sup>n</sup>) < O(n!)
* P: efficiently solvable, NP: efficiently verifiable (formally: solvable on a non-deterministic Turing machine), NP-hard: every problem from NP can be reduced to this problem in polynomial time, NP-complete: in NP-hard and in NP. Efficient = polynomial complexity. [P vs NP](https://en.wikipedia.org/wiki/P_versus_NP_problem) problem. If any NP-complete problem (e.g., graph coloring, Boolean satisfiability) could be solved in polynomial time, then P = NP.

[Amortized analysis](https://en.wikipedia.org/wiki/Amortized_analysis) looks at the entire execution sequence, not just the worst-case scenario.

* Aggregate analysis: T(n)/n for a total cost T of n operations
* Accounting method: saving credit from costly operations to speed up other operations
* Potential method: like the accounting method but with a custom function


### Graphs

* Bipartite: two disjoint, independent sets
* Complete graph: every pair of vertexes is adjacent, no loops
* Strongly connected: every 2 vertexes are reachable from each other
* Tree: connected, acyclic, undirected graph


### Data structures

#### Basic

Average cases for time complexity are presented.
BST is assumed to be balanced, hashing a simple item is assumed to be constant-time.
For the hash table the worst-case for all operations is O(n).

Structure  | Access   | Search   | Insert/delete  | Space
---------- | -------- | ---------| -------------- | -------
Array      | O(1)     | O(n)     | O(n)           | O(n)
List       | O(n)     | O(n)     | O(1)           | O(n)
BST        | O(log n) | O(log n) | O(log n)       | O(n)
Hash table | O(1)     | O(1)     | O(1)           | O(n)

##### Binary search tree

* [AVL](https://en.wikipedia.org/wiki/AVL_tree): first self-balancing BST. Height of two child subtrees differs by at most 1. In order to balance after a regular insertion of new node w: travel up to the root to find the first unbalanced node z. Rotate subtree rooted with z: 4 cases based on node z and its child/grandchild: a) y is left, x is left (on the path to w), b) left-right, c) right-left, d) right-right.

* [Red-black](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree): each node is R or B, the root is B. If node is R, both children are B. Any path from node to any leaf (NIL, B) has the same number of black nodes.

* [Treap](https://en.wikipedia.org/wiki/Treap): BST with priorities maintained in a heap. Searching is just like BST, insertion: generate random priority, add leaf at a regular position, use rotations in order to restore the max-heap property.

##### Heap

[Heap](https://en.wikipedia.org/wiki/Heap_(data_structure)): priority queue, max-heap or min-heap. Adding: add at the bottom, continue swapping with parent (sifting up). Deleting: swap root with the last leaf, sift down the new root. Various kinds of heaps exist: Brodal, Fibonacci, etc.

#### String matching

* [Trie](https://en.wikipedia.org/wiki/Trie): a tree in which the position of a node describes the associated value, search is proportional to the pattern length, that is O(m).

* [Suffix array](https://en.wikipedia.org/wiki/Suffix_array): stores indexes of sorted suffixes from the input text, search is O(m log n), space is around 5n.

* [Suffix tree](https://en.wikipedia.org/wiki/Suffix_tree): a compacted trie which stores all suffixes of the input string, search is O(m), space is around 10n.


### Algorithms

* [Brute-force](https://en.wikipedia.org/wiki/Brute-force_search): exhaustive search, checking all solution candidates.

* [Divide and conquer](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithm): recursively breaking a problem into non-overlapping subproblems. Examples: quicksort, mergesort.

* [Dynamic programming](https://en.wikipedia.org/wiki/Dynamic_programming): solving simpler subproblems and storing solutions, e.g., Fibonacci sequence with [memoization](https://en.wikipedia.org/wiki/Memoization) (result caching). Here the problems are overlapping (unlike in D&C).

* [Greedy algorithm](https://en.wikipedia.org/wiki/Greedy_algorithm): makes a locally optimal choice at each step.

* [Las Vegas](https://en.wikipedia.org/wiki/Las_Vegas_algorithm) vs [Monte Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_algorithm): LV is a randomized algorithm which always produces a correct result or informs about the failure (it gambles with computational resources), MC is a randomized algorithm which might report an incorrect result (it gambles with result accuracy).

#### Graphs

* [A*](https://en.wikipedia.org/wiki/A*_search_algorithm): maintain a closed and open set (open has the starting node at the beginning). While open is not empty, take current from open with the lowest heuristic estimate. Finish if current is the goal, otherwise move it to closed and expand all its neighbors. Ignore neighbors in the closed set (already visited). Finish if current is the goal. Heuristic must be admissible (not overestimating) for the algorithm to find an optimal solution. Example of a [best-first](https://en.wikipedia.org/wiki/Best-first_search) search, where the most promising node (based on the heuristic) is expanded first. Bidirectional variants (searching both from the start and from the goal) exist.

* [B*](https://en.wikipedia.org/wiki/B*): related to A*, uses interval (pessimistic, optimistic) estimates which contain the true value for expanding the nodes.

* [D*](https://en.wikipedia.org/wiki/D*): searches backwards from the goal, uses additional node states such as raise and lower. This allows for handling obstacles more effectively and updates estimates as these obstacles are approached. Alternative D* lite is more commonly used.

* [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm): specific case of A* without a heuristic. A common variant finds shortest paths between the start and all other nodes in the graph.

* [Coloring](https://en.wikipedia.org/wiki/Graph_coloring): labeling where no adjacent vertexes share a label.

* [TSP](https://en.wikipedia.org/wiki/Travelling_salesman_problem): find the shortest Hamiltonian cycle (visits each node exactly once and returns to the start, cf. [Eulerian path](https://en.wikipedia.org/wiki/Eulerian_path) which visits each edge exactly once). The problem is NP-hard, brute force solution takes O(n!), dynamic programming approach takes O(n<sup>2</sup> 2<sup>n</sup>).

* [Voronoi diagram](https://en.wikipedia.org/wiki/Voronoi_diagram): partitioning into regions based on a distance to the closest point.

#### Machine learning

Supervised (input data is labeled), unsupervised (input data is unlabeled), reinforced (maximizing reward based on actions).
Applications:

* [Classification](https://en.wikipedia.org/wiki/Statistical_classification) (discrete)
* [Regression](https://en.wikipedia.org/wiki/Regression_analysis) (continuous)
* [Clustering](https://en.wikipedia.org/wiki/Cluster_analysis)
* [Density estimation](https://en.wikipedia.org/wiki/Density_estimation)

Techniques:

* [ANN](https://en.wikipedia.org/wiki/Artificial_neural_network): artificial neural network. Recurrent networks have backward connections which create a system with memory.
* [Association rules](https://en.wikipedia.org/wiki/Association_rule_learning): created mostly based on frequency of appearance, e.g., `{onions, potatoes} => {burger}`.
* [Decision tree](https://en.wikipedia.org/wiki/Decision_tree_learning): sets of rules. Useful for distinct features, might create human-readable models. Multiple decision trees built on randomly selected subsets of data can form a random forest.
* [Deep learning](https://en.wikipedia.org/wiki/Deep_learning): using multiple layers of nonlinear processing units. Levels correspond to different levels of abstraction and form a hierarchy of concepts. In other words, learning partially consists in finding data representations.
* [Hidden Markov model](https://en.wikipedia.org/wiki/Hidden_Markov_model): models a Markov process (probability of each next state depends only on the previous state) with hidden states.
* [Naive Bayes classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier): naive means that features are independent of one another.
* [SVM](https://en.wikipedia.org/wiki/Support_vector_machine): separate data by hyperplanes with the largest margin. Kernel functions allow for implicit mapping into higher dimensions in order to ensure data segregation. Directly applicable only to binary problems.

#### Sorting

* [Bubble sort](https://en.wikipedia.org/wiki/Bubble_sort): best O(n), avg O(n²), worst O(n²)
* [Insertion sort](https://en.wikipedia.org/wiki/Insertion_sort): best O(n), avg O(n²), worst O(n²)
* [Selection sort](https://en.wikipedia.org/wiki/Selection_sort): best, avg, worst O(n²)
<br />

* [Heapsort](https://en.wikipedia.org/wiki/Heapsort): best, avg, worst O(n log n)
* [Mergesort](https://en.wikipedia.org/wiki/Merge_sort): best, avg, worst O(n log n)
* [Radix sort](https://en.wikipedia.org/wiki/Radix_sort): best, avg, worst O(w n)
* [Quicksort](https://en.wikipedia.org/wiki/Quicksort): best O(n log n), avg O(n log n), worst O(n²), related: [quickselect](https://en.wikipedia.org/wiki/Quickselect), finds k-th smallest element in O(n) avg time.

#### String matching

##### Exact

* [Aho-Corasick](https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm): a finite state machine which resembles a trie. Matches multiple queries at once while sliding over the text.

* [Boyer-Moore](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_string_search_algorithm): begin matching from the end of the pattern and jump forward based on mismatches. After preprocessing, the size of each shift can be determined in constant time: align the text with the rightmost occurrence of current char in P or shift the pattern by its total length. Worst case is O(nm + δ).

* [KMP](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm): for each mismatch at position i in the pattern, shift P by i - l, where l is the length of the longest proper prefix of P[0, i − 1] which is also a suffix of P[0, i − 1] and start matching from position l in the pattern. Worst case is O(n + m).

* [Rabin-Karp](https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm): rolling hash, worst case is O(nm).

* [Shift-or](https://en.wikipedia.org/wiki/Bitap_algorithm): based on bit-parallelism, pattern length must be smaller than the word size. Computes a mismatch mask for each character from the alphabet with unset bits corresponding to positions of this character in the pattern. At each step, the state mask is shifted and or-ed with the mask for the current character from the text.

##### Approximate

* [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance): counts the number of mismatching characters at corresponding positions.

* [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance): counts the number of single-character edits (insert, delete, substitute) needed to transform one word into another.

* [Needleman-Wunsch](https://en.wikipedia.org/wiki/Needleman%E2%80%93Wunsch_algorithm): a dynamic programming algorithm for calculating an optimal global alignment (whole query and whole text). It can use a custom similarity matrix.

* [Smith-Waterman](https://en.wikipedia.org/wiki/Smith%E2%80%93Waterman_algorithm): similar to N-W above, but computes local alignment (whole query and a substring of text).

#### Trees

* [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm): minimum spanning tree. Divide all nodes into a forest, always take the shortest edge, span only if spanning two distinct trees, otherwise discard.

* [Traversal](https://en.wikipedia.org/wiki/Tree_traversal): depth-first search (DFS: pre-order, in-order, post-order), breadth-first search (BFS, use a priority queue based on depth).


### Design patterns

The following summary is based on [Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern) pages.

#### Creational

* [Abstract factory](https://en.wikipedia.org/wiki/Abstract_factory_pattern): encapsulate individual factories under a generic interface.

* [Builder](https://en.wikipedia.org/wiki/Builder_pattern): separate construction from representation, construct an object in stages.

* [Dependency injection](https://en.wikipedia.org/wiki/Dependency_injection): supply a dependency of an object from outside (for instance by setting a private variable via a setter).

* [Factory](https://en.wikipedia.org/wiki/Factory_method_pattern): use functions of a factory in order to create objects instead of using their constructors.

* [Lazy initialization](https://en.wikipedia.org/wiki/Lazy_initialization): delay performing the operation (which is usually expensive) until its result is needed.

* [Multiton](https://en.wikipedia.org/wiki/Multiton_pattern): a registry (map) of singletons.

* [Object pool](https://en.wikipedia.org/wiki/Object_pool_pattern): store a pool of objects which are ready to be used so that no time is spent on initializing them when needed (e.g., thread pool).

* [Prototype](https://en.wikipedia.org/wiki/Prototype_pattern): create new objects from a skeleton. Prototypes may be used by an abstract factory.

* [Singleton](https://en.wikipedia.org/wiki/Singleton_pattern): only a single object instance can exist.

#### Structural

* [Adapter](https://en.wikipedia.org/wiki/Adapter_pattern): a wrapper which provides an alternative interface to the existing code.

* [Bridge](https://en.wikipedia.org/wiki/Bridge_pattern): decouples abstraction from implementation in order to facilitate changes (created upfront unlike the adapter).

* [Composite](https://en.wikipedia.org/wiki/Composite_pattern): treating multiple objects as a single object.

* [Decorator](https://en.wikipedia.org/wiki/Decorator_pattern): dynamically add behavior to an individual object without affecting the behavior of other objects (i.e. alter the behavior at runtime).

* [Extension](https://kotlinlang.org/docs/reference/extensions.html): allows for adding new functionality to a class without inheritance (e.g., extension functions in Kotlin).

* [Facade](https://en.wikipedia.org/wiki/Facade_pattern): a higher-level interface which is easier to use.

* [Flyweight](https://en.wikipedia.org/wiki/Flyweight_pattern): use sharing to support large numbers of lightweight similar objects efficiently.

* [Marker](https://en.wikipedia.org/wiki/Marker_interface_pattern): use an empty interface to indicate specific behavior (e.g., Serializable).

* [Proxy](https://en.wikipedia.org/wiki/Proxy_pattern): used in order to control access to an object or provide additional functionality. 

* [Twin](https://en.wikipedia.org/wiki/Twin_pattern): models multiple inheritance in languages that do not support it (two closely coupled subclasses, each derived from one superclass).

#### Behavioral

* [Blackboard](https://en.wikipedia.org/wiki/Blackboard_(design_pattern)): knowledge sources publish potential solutions on the blackboard, the control component is in between.

* [Chain of responsibility](https://en.wikipedia.org/wiki/Chain-of-responsibility_pattern): a chain of processing objects receives the commands which are handled or passed along. Essentially if..elif..else which can be dynamically reconfigured.

* [Command](https://en.wikipedia.org/wiki/Command_pattern): object encapsulates all information needed to perform an action at a later time, including the receiver.

* [Interpreter](https://en.wikipedia.org/wiki/Interpreter_pattern): the use of a [domain-specific](https://en.wikipedia.org/wiki/Domain-specific_language) language (DSL), e.g., SQL, user interface descriptions.

* [Iterator](https://en.wikipedia.org/wiki/Iterator_pattern): decouples algorithms from containers, since container elements can be accessed with the use of an iterator (without exposing data representation).

* [Mediator](https://en.wikipedia.org/wiki/Mediator_pattern): encapsulates communication between objects, reduces coupling.

* [Memento](https://en.wikipedia.org/wiki/Memento_pattern): checkpointing, allows for restoring a previous state via rollback.

* [Null object](https://en.wikipedia.org/wiki/Null_object_pattern): also called a nullable type, allows for avoiding problems with null dereference.

* [Observer](https://en.wikipedia.org/wiki/Observer_pattern): publish-subscribe, signals-slots, event-driven, observers are notified of any changes.

* [Servant](https://en.wikipedia.org/wiki/Servant_(design_pattern)): provides functionality (methods) to a group of classes (which hence do not need to implement this functionality), objects for which the servant provides the service are taken as parameters.

* [Specification](https://en.wikipedia.org/wiki/Specification_pattern): combining rules using Boolean operators, used mostly for data filtering.

* [State](https://en.wikipedia.org/wiki/State_pattern): implement state machine where each state is a derived class calling parent interface methods.

* [Strategy](https://en.wikipedia.org/wiki/Strategy_pattern): enables selecting algorithm type or parameters at runtime (e.g., validation algorithm based on incoming data).

* [Template method](https://en.wikipedia.org/wiki/Template_method_pattern): base class implements basic steps of an algorithm, specifics (variants) are implemented in derived classes.

* [Visitor](https://en.wikipedia.org/wiki/Visitor_pattern): separate algorithm from object structure on which it operates, allows for defining new operations without changing elements on which it operates. Visitor takes concrete elements as arguments.


### Architectural patterns

* [Broker](https://en.wikipedia.org/wiki/Broker_pattern): provides coordination among components, for instance in between the client and servers.
* [Client-server](https://en.wikipedia.org/wiki/Client%E2%80%93server_model): servers provide a service and clients request a service.
* [Layered](https://en.wikipedia.org/wiki/Layer_(object-oriented_design)): levels of abstraction, for instance UI layer, service, domain (business logic), persistence layer, e.g., general desktop app.
* [Master-slave](https://en.wikipedia.org/wiki/Master/slave_(technology)): master has control over the slaves, sometimes can be configured dynamically.
* [P2P](https://en.wikipedia.org/wiki/Peer-to-peer): peer-to-peer, equally privileged participants.
* [Pipe-filter](https://en.wikipedia.org/wiki/Pipeline_(software)): `src | pipe1 | filter1 | pipe2 | filter2 | sink`, e.g., compiler. Pipes pass the data along and filters filter the data.

#### MVC

[Model-view-controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

* Model: data + state.
* View: lean, rendering UI, loosely coupled, not knowing what to do when the user presses the button (only forwards data).
* Controller: receives the input from the view and interacts with the model (e.g., activity in Android).

Problem is with the controller which is tightly coupled with a view and may get bloated, since most of the logic is there.

#### MVP

[Model-view-presenter](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter)

* Model: the same as in MVC.
* View: it is now up to the view which is a bit smarter than in MVC to determine which functions from the presenter to call.
* Presenter: is like a controller but is just an interface, not tied to the view in order to allow more flexibility.

#### MVVM

[Model-view-viewmodel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)

* Model: the same as in MVC.
* View: binds to the observables that are exposed by the viewmodel.
* Viewmodel: has observables for the view and allows the view to pass events to the model.


### Language-related concepts

* Binding: early = at compile time (e.g., overloading), late (dynamic) = at run time (e.g., overriding).
* Declarative (functional, logic, reactive) vs imperative languages (procedural, object-oriented).
* Introspection: ability to examine type or properties at runtime.
* Monkey patching: dynamic replacement of attributes at runtime.
* Reflection: modification of program structure at runtime.
* Single dispatch (depends on object type as in C++) vs double dispatch (depends both on object type and parameters).
* Static dispatch (e.g., function overloading) vs dynamic dispatch (for dynamic dispatch, declare a C++ method as virtual).

#### Object-oriented terminology

* [Abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science)): employing representations which contain only relevant information.
* [Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)): hiding and restricting access to certain information.
* [Friend function](https://en.wikipedia.org/wiki/Friend_function): defined outside a class but can access internal (private, protected) data.
* [Inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)): basing a class on another class, retaining its properties. Creates a parent-child (superclass-subclass) relation.
* [Interface](https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming)): a collection of methods (mostly abstract), conceptually a protocol for communication (may form an API).
* [Overloading vs overriding](https://stackoverflow.com/questions/837864/java-overloading-vs-overriding): overloading refers to multiple methods with the same name but different parameters (return value doesn't matter, overloading is resolved at compile time), overriding refers to the redefinition of a function from the base class in the derived class (overriding is resolved at run-time).
* [Polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)): more than one form, examples: function overloading (ad-hoc polymorphism), generics, inheritance.
* [Virtual function](https://en.wikipedia.org/wiki/Virtual_function): a function which can be overridden, it is selected via dynamic dispatch.


### Principles and abbreviations

* [ACID](https://en.wikipedia.org/wiki/ACID): for transactions: atomicity (all or nothing), consistency (one valid state to another), isolation (concurrent execution same result as sequential), durability (once committed remains so).

* [ABI](https://en.wikipedia.org/wiki/Application_binary_interface): application binary interface, determines how components "talk" to each other at the level of machine code.

* [API](https://en.wikipedia.org/wiki/Application_programming_interface): application programming interface, determines how components "talk" to each other at the level of source code.

* [Boilerplate code](https://en.wikipedia.org/wiki/Boilerplate_code): a part of source code which is reused in multiple places. It is generally desirable to reduce the amount of boilerplate code.

* [Broken windows theory](https://en.wikipedia.org/wiki/Broken_windows_theory): bad code encourages more bad code.

* [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem): only 2/3 guarantees are simultaneously possible: consistency (every read receives the most recent write or error), availability (every request has a response), partition tolerance (system works even if messages are dropped).

* [CLI](https://en.wikipedia.org/wiki/Command-line_interface): command-line interface.

* [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete): create, read, update, delete, 4 basic functions of persistent storage.

* [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself): don't repeat yourself, i.e. avoid redundancy.

* [KISS](https://en.wikipedia.org/wiki/KISS_principle): keep it simple, stupid.

* [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter): principle of least knowledge, each unit should have knowledge only about closely related units (advocates loose coupling).

* [Lint](https://en.wikipedia.org/wiki/Lint_(software)): tools which analyze source code in order to find bugs, errors, and suspicious constructs. There exits many linters for various languages and platforms. Examples: `Cppcheck` for C++, `pylint` for Python.

* [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method): project planning: must have, should have, could have, won't have.

* [Naming convention](https://en.wikipedia.org/wiki/Naming_convention_(programming)): determines how the identifiers (names) are written for functions, variables, etc. Examples: `camelCase`, `PascalCase`, `snake_case`, `kebab-case`.

* [Not invented here](https://en.wikipedia.org/wiki/Not_invented_here): avoiding using products, guidelines, etc. created outside the company.

* [Occam's razor](https://en.wikipedia.org/wiki/Occam%27s_razor): one should select the answer that makes the fewest assumptions (simpler theories are preferable).

* [Principle of least astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment): components of the system should behave in an expected way, might apply to both the UI and the source code.

* [Programming style](https://en.wikipedia.org/wiki/Programming_style): a set of rules for writing the source code. A specific set is called a [coding convention](https://en.wikipedia.org/wiki/Coding_conventions). It is often language-specific.

* [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization): resource acquisition is initialization, meaning that holding a resource is tied to the lifetime of an object. In C++ realized through constructor/destructor.

* [Reinventing the wheel](https://en.wikipedia.org/wiki/Reinventing_the_wheel): duplicating a common, known method.

* [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop): read-eval-print loop, a program which reads and evaluates a set of instructions entered by the user, followed by printing the result.

* [RFC](https://en.wikipedia.org/wiki/Request_for_Comments): Request for Comments, a kind of a pre-standardization or standardization document in the Internet-related context.

* [SFINAE](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/SFINAE): substitution failure is not an error. Removes functions which do not yield valid template instantiations from a set of overloaded functions.

* [Short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation): following arguments of a Boolean expression are evaluated only when the evaluation of previous arguments is not sufficient to determine the result.

* [SOLID](https://en.wikipedia.org/wiki/SOLID): single responsibility (per class), open/closed (open for extension, closed for modification, e.g., inheritance), Liskov substitution (subclass can be used as if it were its parent), interface segregation (expose only the required methods to clients), dependency inversion (program to an interface, not to an implementation).

* [SSOT](https://en.wikipedia.org/wiki/Single_source_of_truth): single source of truth, meaning that each data element is stored exactly once.

* [WORA](https://en.wikipedia.org/wiki/Write_once,_run_anywhere): write once, run anywhere, a Java slogan indicating that a Java program can be run on any device with a [JVM](https://en.wikipedia.org/wiki/Java_virtual_machine).

* [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better): less functionality is sometimes preferable (e.g., easier to use).

* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it): you ain't gonna need it, that is don't add functionality until necessary.


### Project planning

* [Brook's law](https://en.wikipedia.org/wiki/Brooks%27s_law): an observation that "adding human resources to a late software project makes it later".

* [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration): merging all working copies several times a day in order to mitigate integration problems.

* [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery): short cycles, software can be released at short notice.

* [Crunch time](https://en.wikipedia.org/wiki/Video_game_developer#%22Crunch_time%22): a period of intense work, usually before reaching a milestone.

* [Death march](https://en.wikipedia.org/wiki/Death_march_(project_management)): a project which is set to fail or which requires unsustainable overwork.

* Development stages: pre-alpha, alpha (internal testing), beta (external testing, mostly bugfixes), release candidate (gamma, [feature freeze](https://en.wikipedia.org/wiki/Freeze_(software_engineering)), only the most important bugfixes).

* [Neutral build](https://en.wikipedia.org/wiki/Neutral_build): done in a neutral environment (outside deployment), catches errors such as different environmental variables, unchecked files, etc.

* [Nightly build](https://en.wikipedia.org/wiki/Daily_build): automated neutral build, mostly done when no one is working. Sometimes also called a daily build. It is often performed on multiple platforms, various emulated hardware, etc. and coupled with automated testing.

#### Things to consider

1. Specification, possibly start with abstract description and work towards the details.
1. Select the technologies and the development process.
1. Define features, perhaps in connection with the technologies.
1. Define the timeline: task planning, delegation, select a team, divide responsibilities, agree on how progress/success will be measured/defined (formulate the definition of "done").
1. Compile code guidelines.
1. Before the start: check if we have everything we need (resources, etc.).

#### Scrum

[Scrum](https://en.wikipedia.org/wiki/Scrum_(software_development)): usually 3-9 people in a team.
Work is divided into sprints, each roughly 2 weeks, with daily 15-minute stand-ups (people stand in order to keep the meeting short).
Tasks for each sprint are usually estimated in terms of story points, sometimes using the [planning poker](https://en.wikipedia.org/wiki/Planning_poker) technique.
Scrum is an example of [agile](https://en.wikipedia.org/wiki/Agile_software_development) development: iterative, incremental, flexible.

Parties in Scrum:

* Development team
* Product owner = stakeholders
* Scrum master = servant-leader who helps the team

Meetings in Scrum:

* daily stand-up (daily Scrum): each member summarizes what they achieved and what they will do in the future
* sprint planning: describing and assigning tasks for the next sprint
* sprint review: showing what was achieved during the sprint
* sprint retrospective: only Scrum team members reflecting on how the sprint went
* product backlog refinement

A related agile method is [Kanban](https://en.wikipedia.org/wiki/Kanban_(development)).
It is continuous, the scope is more fluid, and there is no set cadence (speed).
Issues move between development stages such as "testing", "done", etc.

### Testing

A unit in a [unit test](https://en.wikipedia.org/wiki/Unit_testing) could be an entire module or interface or an individual method.
Unit tests are often combined with [matchers](https://en.wikipedia.org/wiki/Hamcrest) (Hamcrest) which extend simple assertions and allow for the use of a declarative style.

Common terms include:

* [A/B testing](https://en.wikipedia.org/wiki/A/B_testing): a controlled experiment (i.e. ideally varying only in what is tested) of two variants, e.g., testing two website designs for user engagement.

* [Behavior-driven development](https://en.wikipedia.org/wiki/Behavior-driven_development) (BDD): extension of TDD where tests are based on scenarios and descriptions, for example using the [given-when-then](https://en.wikipedia.org/wiki/Given-When-Then) approach.

* [Black-box testing](https://en.wikipedia.org/wiki/Black-box_testing): testing without knowing the internals.

* [Code coverage](https://en.wikipedia.org/wiki/Code_coverage): describes how much of source code is executed by unit tests. Could be measured in terms of functions, statements, branches, etc.

* [Fuzz test](https://en.wikipedia.org/wiki/Fuzzing): testing with invalid, unexpected, or random data. Related is [monkey testing](https://en.wikipedia.org/wiki/Monkey_testing) where random input is supplied to the program.

* [Hallway testing](https://en.wikipedia.org/wiki/Usability_testing#Hallway_testing): asking a random person (one passing in a hallway) to try a given feature.

* [Mock](https://en.wikipedia.org/wiki/Mock_object): used instead of a real object, also called [stub](https://en.wikipedia.org/wiki/Test_stub) (definitions might vary).

* [Regression testing](https://en.wikipedia.org/wiki/Regression_testing): checking whether the system still works correctly after introducing changes (configuration, patch, etc.).

* [Smoke test](https://en.wikipedia.org/wiki/Smoke_testing_(software)): sanity test such as checking whether the program runs at all.

* [Spy](https://stackoverflow.com/questions/12827580/mocking-vs-spying-in-mocking-frameworks): related to a mock, this is usually a real object whose behavior is modified in some way, while a mock is all fake.

* [Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) (TDD): tests are written first and all features must pass specific tests.

* [White-box testing](https://en.wikipedia.org/wiki/White-box_testing): testing internal structure rather than a functionality/interface.

#### Unit testing in C++

Accessing private members can be realized using various methods. In general, it is discouraged in favor of testing only the public interface. If necessary, once can use, e.g., [friend classes](https://stackoverflow.com/questions/14186245/unit-testing-c-how-to-test-private-members/14186634), shown below.

```cpp
#ifndef TESTED_WHITEBOX
#define TESTED_WHITEBOX
#endif

class Tested
{
public:

private:
    TESTED_WHITEBOX
}
```

```cpp
#define TESTED_WHITEBOX \
    friend class Testing;

class Testing
{
    // call private functions from Tested
}
```
Example in C++ using the [Catch2](https://github.com/catchorg/Catch2) library:

```cpp
// Inserts the necessary main function.
// It is recommended that this code should be in a separate file for faster compilation.
#define CATCH_CONFIG_MAIN 
#include "catch.hpp"

#include <stdexcept>

using namespace std;
using Catch::Matchers::VectorContains;

// Test case name, test case group (allows for running multiple grouped test cases).
TEST_CASE("is addition correct", "[math]")
{
    // Require = checking for true (use CHECK not to stop on error).
    REQUIRE([](int x, int y) { return x + y; }(2, 6) == 8);

    // Check whether exception of a given type is thrown.
    REQUIRE_THROWS_AS([]() { throw invalid_argument("test"); }(), invalid_argument);

    // There are also some matchers available in catch that can be used with REQUIRE_THAT.
    vector<int> vec{ 1, 2, 3 };
    REQUIRE_THAT(vec, VectorContains(2));
}
```


### Useful Linux commands

#### General

* `cat [file]` – print file contents

* `chmod [XXX] [file]` – change permissions to `[XXX]` (owner, group, anybody) for `[file]`. 4 = read, 2 = write, 1 = execute (can be combined). Example: `chmod 664 run.sh` sets read and write (`4 | 2 = 6`) permissions for owner and group and read permission for anybody.

* `chown alex *.txt` – set user `alex` to be the owner of all `.txt` files in the current directory

* `df -h` – disk usage in human-readable

* `find / -name "*.txt" -size +256c 2> /dev/null` – find all files with .txt extension which are larger than 256 bytes (type `-256c` for smaller than) while ignoring error messages

* `grep ^alex /etc/passwd | cut -d: -f1` – grep lines starting with "alex", delimit on ":" and print the first field

* `grep bash$ /etc/passwd | head -n1 | sed 's/:/ /g'` – grep lines ending with "bash", print the first line, replace each ":" with " "

* `grep -nr 'pattern' .` – [recursively](https://stackoverflow.com/questions/4121803/how-can-i-use-grep-to-find-a-word-inside-a-folder) search for a pattern in a current directory, print line numbers

* `ls -lah` – list current directory with hidden files and details in human-readable

* `man gcc | grep [-]std=c++11 -C2` – search for a switch in a manpage and show 2 lines around the result

* `mv [src] [dst]` – move file `[src]` to `[dst]`, can be used for renaming

* `nohup [cmd] &` – run `[cmd]` in the background immune to hangups (i.e. it won't be killed if the user logs off), appends output of this command to `nohup.out`

* `ps -e` – show all running processes, can be used to determine the PID for a later call to `kill -9 [PID]` in order to kill a process which is associated with `[PID]`

* `rm -rf [dir]` – remove `[dir]` recursively without prompting

* `rm $(find . -name "*.txt")` – argument list might be too long, using xargs which converts input into arguments of a command: `find . -name "*.txt" | xargs rm` or `find . -name "*.txt" | xargs -i{} rm {}` (the latter calls remove multiple times with a single argument)

* `touch [file]` – create `[file]`

* `whereis [cmd]` – check the location of `[cmd]`

#### Compression

* `tar -xzf [in]` – extract, gunzip (j = bzip), input file `[in]`

* `unzip [file]`

* `zip [out] [file1] [file2]`

#### Conversions

* `dot -Tpdf [in].dot -o [out].pdf` – convert dot (graph) file `[in]` to `[out].pdf`

* `pdfcrop --margins '0 0 0 0' [in].pdf [out].pdf` – crop pdf file `[in].pdf`, write to `[out].pdf`

* `rsvg-convert -f pdf -o [out].pdf [in]` – convert SVG file `[in]` to `[out].pdf`

#### Net

* `host [url]` – get IP for `[url]`

* `scp [login]@[url]:[path] .` – copy file from remote (located at `[path]` at remote) to the current directory at the local machine

* `wget [url]` – download a single file from `[url]`

* `wget -m -e robots=off --no-parent [url]` – download recursively from `[url]`

* `whois [IP]` – get information about `[IP]`

#### Packages

* `apt-get update` – update package index

* `apt-get dist-upgrade` – install update and satisfy dependencies

* `dpkg --listfiles [pkg]` – list all files from package `[pkg]`

* `update-alternatives --config [pkg]` – select a different version for `[pkg]`


C++
--------------------

[C++](https://en.wikipedia.org/wiki/C%2B%2B): compiled, static typing, object-oriented.
[Compilation](https://stackoverflow.com/questions/6264249/how-does-the-compilation-linking-process-work) proceeds as follows:

1. Preprocessing: handling preprocessor directives, i.e. parsing defines, includes, macros, etc. Produces a [translation unit](https://en.wikipedia.org/wiki/Translation_unit_(programming)) (input to a compiler) for each source file.
1. Compilation: produces object files (.o). These can be grouped into a static library (.a or .lib Linux/Windows). Object files can refer to symbols that are declared but not defined.
1. Linking: combines object files into an executable or a dynamic library (.so or .dll Linux/Windows, sometimes .lib is also used).

### Basic

* `assert(1 == 1 == 1)` doesn't fail, `assert(4 == 4 == 1)` doesn't fail, `assert(4 == 4 == 4)` fails, assert `assert(1 == 4 == 4)` fails.

* Abstract class has pure virtual functions: `virtual void fun() = 0;`. Each pure virtual function must be overridden for the class to be instantiated.

* Class has private fields/funs by default, struct has public fields/funs by default.

* Constructor types: default (has no parameters or all parameters have default values), parametric, copy, move. When no constructor is defined by the user, the default constructor is supplied by the compiler.

* References cannot be null, reset or uninitialized.

* [Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)): destructor, copy constructor, copy assignment operator.

* Supports checked exceptions (i.e. exception type is declared explicitly for a function), but this is usually [discouraged](https://blog.philipphauer.de/checked-exceptions-are-evil/).

#### Bitwise operators

There are 6 bitwise operators available:

```cpp
& // and
| // or
^ // xor
~ // not
<< // shift left (same as multiplying by 2)
>> // shift right (same as dividing by 2)
```

```cpp
cout << (7 & 5) << endl; // prints 5 since 0111 & 0101 = 0101
cout << (3 | 4) << endl; // prints 7 since 0011 | 0100 = 0111
cout << (7 ^ 5) << endl; // prints 2 since 0111 ^ 0101 = 0010
cout << (~5) << endl;    // prints -6 since ~0...00101 = 1...11010
cout << (3 << 1) << endl; // prints 6 since 0011 << 1 = 0110
cout << (6 >> 1) << endl; // prints 3 since 0110 >> 1 = 0011
```

#### Casting

There are 4 following kinds of [casts](http://people.scs.carleton.ca/~dehne/projects/cpp-doc/tutorial/tut5-4.html).

* **Static cast**: conversions which can be implicitly performed. 

```cpp
float f = 1.5;
int i = 1;

cout << static_cast<int>(f) << endl; // prints 1
cout << static_cast<float>(i) << endl; // prints 1
``` 

Works also for class pointer casting.

```cpp
struct A 
{
    virtual void print() { cout << "A" << endl; }
};
struct B : public A 
{
    virtual void print() { cout << "B" << endl; }
};

A *abPtr = static_cast<A *>(bPtr); // Up the hierarchy.
abPtr->print(); // prints B

B *bPtr2 = static_cast<B *>(abPtr); // Down the hierarchy.
bPtr2->print(); // prints B

// B *bPtr3 = aPtr; // This would give error (invalid conversion).

B *bPtr3 = static_cast<B *>(aPtr); // Down the hierarchy, bad cast (not B). 
bPtr3->print(); // Hence prints A.
```

* **Dynamic cast**: can be used for casting polymorphic classes up and down the hierarchy, checks if the cast is valid.

```cpp
struct A 
{
    virtual void print() { cout << "A" << endl; }
};
struct B : public A 
{
    virtual void print() { cout << "B" << endl; }
};

A *aPtr = new A;
B *bPtr = new B;

A *abPtr = dynamic_cast<A *>(bPtr); // Up the hierarchy, good cast = works the same as static_cast.
abPtr->print(); // prints B

B *bPtr2 = dynamic_cast<B *>(abPtr); // Down the hierarchy, good cast = works the same as static_cast.
bPtr2->print(); // prints B

B *bPtr3 = dynamic_cast<B *>(aPtr); // Down the hierarchy, bad cast (not B), returns null. 
if (bPtr3 != nullptr)
{
    bPtr3->print(); // This is not run.
}
```

* **Reinterpret cast**: casts any pointer to any other pointer type or int. Unlike static cast, doesn't work for, e.g., casting between int and float.

```cpp
struct A
{
    virtual void print() { cout << "A" << endl; }
};
struct B : public A 
{
    virtual void print() { cout << "B" << endl; }
};

A *aPtr = new A;
B *bPtr = new B;

A *abPtr = reinterpret_cast<A *>(bPtr); // Up the hierarchy, good cast = works the same as static_cast.
abPtr->print(); // prints B

B *bPtr2 = reinterpret_cast<B *>(abPtr); // Down the hierarchy, good cast = works the same as static_cast.
bPtr2->print(); // prints B

B *bPtr3 = reinterpret_cast<B *>(aPtr); // Down the hierarchy, bad cast (not B), works the same as static_cast. 
bPtr3->print(); // Hence prints A.

long pVal = reinterpret_cast<long>(aPtr);
cout << hex << pVal << endl; // Prints aPtr value (i.e. memory address) in hex.

reinterpret_cast<A *>(pVal)->print(); // prints A

C *cPtr = new C;
A *badAPtr = reinterpret_cast<A *>(cPtr); // Static or dynamic cast here would not compile.

badAPtr->print(); // Fails at runtime.
```

* **Const cast**: can add or remove the const modifier.

```cpp
struct A { };
const A *acPtr = new A;

// Stripping the const -- this would not work without the cast.
A *aPtr = const_cast<A *>(acPtr);

const A *aPtr2 = const_cast<const A *>(aPtr); // The cast is actually redundant here.
```

#### Data parsing

Data parsing in C++ can be achieved, e.g., using the [Boost](https://www.boost.org/) library.
Below is an example of parsing a csv string in C++ and in Python.

```cpp
#include <boost/algorithm/string.hpp>

string str = "1,2,3\n4,5,6";
vector<string> lines;

boost::split(lines, str, boost::is_any_of("\n"));
cout << lines.size() << endl; // prints 2

vector<vector<float>> numbers(lines.size());
for (size_t i = 0; i < numbers.size(); ++i)
{
    vector<string> numberStrings;
    boost::split(numberStrings, lines[i], boost::is_any_of(","));

    for (const string &num : numberStrings)
    {
        numbers[i].push_back(stof(num)); // using stof from C++11
    }
}
```

```python
lines = text.split("\n")
data = [[float(num) for num in l.split(",") if num] for l in lines if l]
```

#### Memory management

`malloc`/`calloc` return NULL on error and they must be matched with `free`/`realloc`.
`new` must be matched with `delete` or `delete[]`, it throws `bad_alloc` on error or use `(std::nothrow)` to return NULL instead.

Placement new uses already allocated memory for constructing an object: 

```cpp
char *buf = new char[sizeof(string)];
string *p = new (buf) string("hi")
```

#### Namespaces

[Namespaces](https://en.wikipedia.org/wiki/Namespace) are used in order to group identifiers and thus avoid [name collisions](https://en.wikipedia.org/wiki/Name_collision).
Note that stuff from the standard library is located under the `std` namespace.
It is generally discouraged to put `using` in a header in order to avoid pollution when the header is included.

Various ways of accessing the `std` namespace:

```cpp
int main()
{
    std::cout << "Hello" << std::endl;
}
```

```cpp
using namespace std;

int main()
{
    cout << "Hello" << endl;
}
```

```cpp
int main()
{
    // Using at function level, must be located before accessing the identifier.
    using namespace std;
    cout << "Hello" << endl;
}
```

```cpp
int main()
{
    // Using at scope level
    {
        using namespace std;
        cout << "Hello" << endl;
    }

    // This wouldn't compile.
    // cout << "Hello" << endl;
}
```

```cpp
struct A
{
    // This is not allowed.
    // using namespace std;

    static void print()
    {
        // Function scope in a member function.
        using namespace std;
        cout << "Hello" << endl;
    }
};

int main()
{
    A::print();
}
```

Namespace declaration and access example:

```cpp
namespace A
{
    namespace B
    {
        int n = 5;
    }
}

namespace C
{
    class string
    {
    public:
        string(const char *argBuf)
            :buf(argBuf)
        { }

        friend std::ostream &operator<< (std::ostream &out, const string &str)
        {
            out << "C::" << str.buf;
            return out;
        }
    private:
        const char *buf;
    };
}

int main()
{
    std::cout << A::B::n << std::endl; // prints 5
    std::cout << std::string("ala") << " " << C::string("ala") << std::endl; // prints "ala C::ala"
}
```

#### Operator overloading

The following example demonstrates overloads for the majority of [operators](https://en.cppreference.com/w/cpp/language/operators).
Note: [binary operators](https://stackoverflow.com/questions/4622330/operator-overloading-member-function-vs-non-member-function) can be realized as member or global (usually friend) functions.
The former are translated as follows: `n1 + n2` -> `n1.operator+(n2)`, so the first (left) operand must be always of class type (i.e. this is less flexible).
If the global function uses only the public interface of the class, there is no need for making it a friend.

Also note: the initializer list `Num(int argN) : n(argN) { }` is useful when members are complex types, as it avoids calling the default constructor. Variables are initialized in the order of their declaration in the class (i.e. not necessarily in the order in the initializer list).

```cpp
class Num
{
public:
    // CONSTRUCTORS AND ASSIGNMENT OPERATORS

    Num() { }
    Num(int argN) : n(argN) { }
    
    // Copy constructor
    Num(const Num &other)
    {
        this->n = other.n;
    }

    // Copy assignment operator
    Num &operator= (const Num &other) // Or pass-by-value for copy-and-swap idiom.
    {
        this->n = other.n;
        return *this;
    }

    // ARITHMETIC (BINARY) OPERATORS

    Num& operator+= (const Num& other)
    {
        n += other.n;
        return *this;
    }

    friend Num operator+ (const Num &t1, const Num &t2)
    {
       return Num(t1.n + t2.n);
    }
    // Alternative variant using the += operator follows.
    // friend Num operator+ (Num t1, const Num &t2)
    // {
    //     return t1 += t2;
    // }
    
    friend Num operator+ (int n, const Num &t2)
    {
       return Num(n + t2.n);
    }

    // Other arithmetic operators (- * /) follow the same scheme as plus above.

    // Bitwise operators can be also overloaded.
    friend Num operator| (const Num &t1, const Num &t2)
    {
        return Num(t1.n | t2.n);
    }

    // UNARY OPERATORS

    Num &operator++ () // postfix ++
    {
        this->n += 1;
        return *this;
    }

    Num operator++ (int) // prefix ++
    {
        Num old(*this); // Invokes the copy constructor.

        operator++();
        return old;
    }

    // Operator-- follows the same scheme as ++ above.

    Num operator- () // unary minus
    {
        return Num(-1 * this->n);
    }

    Num operator! () // logical not
    {
        return Num(-1 * this->n);
    }

    // RELATIONAL OPERATORS

    friend bool operator== (const Num &n1, const Num &n2)
    {
        return n1.n == n2.n;
    }
    // Alternative member variant follows.
    // bool operator== (const Num &other)
    // {
    //     return this->n == other.n;
    // }
    friend bool operator!= (const Num &n1, const Num &n2)
    {
        return !(n1 == n2);
    }

    friend bool operator< (const Num &n1, const Num &n2)
    {
        return n1.n < n2.n;
    }
    friend bool operator<= (const Num &n1, const Num &n2)
    {
        return n1.n <= n2.n;
    }

    // I/O OPERATORS

    friend istream &operator>> (istream &in, Num &num)
    {
        in >> num.n;
        return in;
    }

    friend ostream &operator<< (ostream &out, const Num &num)
    {
        if (num.n == 100)
        {
            cout << "one hundred";
        }
        else
        {
            cout << num.n;
        }

        return out;
    }

private:
    int n;
};

int main()
{
    Num num1 = Num(2) + Num(6);

    // Thanks to the friend overload, this works even when the Num constructor is explicit.
    Num num2 = 2 + Num(6);

    cout << num1 << " " << num2 << endl; // prints 8 8
    
    // This invokes the constructor of Num with 4 as argument.
    // It wouldn't work if the constructor were explicit.
    num2 += 4;

    cout << num1 << " " << num2 << endl; // prints 8 12
    cout << (Num(2) | Num(4)) << endl; // prints 6 (bitwise or)

    ++num1;
    num1++;

    cout << num1 << endl; // prints 10
    cout << -num1 << " " << !num1 << " " << num1 << endl; // prints -10 -10 10

    cout << (num1 == num1) << " " << (num1 == num2) << endl; // prints 1 0
    cout << (num1 != num1) << " " << (num1 != num2) << endl; // prints 0 1
    cout << (num1 < num2) << " " << (num1 <= num2) << endl; // prints 1 1

    cout << Num(100) << endl; // Prints "one hundred" using the overloaded << operator.

    Num num3;
    cin >> num3;
    cout << num3 << endl; // Prints the number entered by the user.
}
```

#### Preprocessor directives

* Useful for [debug print](https://stackoverflow.com/questions/14251038/debug-macros-in-c):

```cpp
#define DEBUG

#ifdef DEBUG
    #define D(code) code
    #define DEBUG_PRINT(msg) (cout << msg << endl)
#else
    #define D(code)
    #define DEBUG_PRINT(msg)
#endif

D(cout << "Hello debug" << endl;)
DEBUG_PRINT("Hello debug 2");
```

* Useful for code selection at compile-time:

```cpp
#define ALG_TYPE 1

#if ALG_TYPE == 1
    cout << "Alg type 1" << endl;
#elif ALG_TYPE == 2
    cout << "Alg type 2" << endl;
#else
    #error Bad ALG_TYPE
#endif
```

* Useful for OS-specific code:

```cpp
#ifdef __linux__
    cout << "Hello Linux" << endl;
#elif _WIN32
    cout << "Hello Windows" << endl;
#else
    #error OS not supported
#endif
```

* Use do-while for correct multi-line expansion:

```cpp
#define PRINT(x, y)               \
do                                \
{                                 \
    cout << "x = " << x;          \
    cout << " y = " << y << endl; \
} while (0)
```

* [Include guards](https://en.wikipedia.org/wiki/Include_guard) prevent double declaration and circular inclusion.

#### Program segments

A program loaded into memory is divided into the following segments.

* [bss](https://en.wikipedia.org/wiki/.bss): uninitialized static variables. Often only the size of this section and no actual data is stored in an executable or object file (the memory is allocated when the program is loaded).
* [Data segment](https://en.wikipedia.org/wiki/Data_segment): initialized static variables. The size depends on the size of variables in source code and does not change at runtime.
* [Heap](https://en.wikipedia.org/wiki/Memory_management#HEAP): dynamic memory allocation.
* [Rodata segment](https://en.wikipedia.org/wiki/Data_segment): initialized constant static variables (read-only data).
* [Stack](https://en.wikipedia.org/wiki/Call_stack): local variables. When subroutines are called, they push the [return address](https://en.wikipedia.org/wiki/Return_statement) onto the stack.
* [Text segment](https://en.wikipedia.org/wiki/Code_segment): executable instructions. This is typically read-only.

#### Templates

Template function with a type:

```cpp
template<typename T> // "typename" or "class" is a keyword for the type
void printVector(const vector<T> &vec)
{
    for (const T &item : vec) { cout << item << endl; }
}

int main() 
{
    printVector<int>({ 1, 2, 3 });
    printVector(vector<int> { 1, 2, 3 });
}
```

Template function with a type and a value:

```cpp
template<typename T, int N> // type int N = 5 in order to provide a default template parameter value
void printVector(const vector<T> &vec)
{
    for (int i = 0; i < N and i < vec.size(); ++i) { cout << vec[i] << endl; }
}

int main() 
{
    printVector<int, 2>({ 1, 2, 3 }); // prints 1 2
}
```

Template class:

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }
    T val;
};

int main() 
{
    Box<int> box(2);
    cout << box.val << endl;
}
```

Template function inside a template class:

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }

    template<int repeat>
    void dumpVal()
    {
        for (int i = 0; i < repeat; ++i)
        {
            cout << val << endl;
        }
    }

    T val;
};

int main() 
{
    Box<int> box(2);
    box.dumpVal<5>(); // Template argument must be a constant.
}
```

Template function inside a template class, definition outside the class:

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }

    template<int repeat>
    void dumpVal();

    T val;
};

// Note that with templates the definition must be visible where the function is instantiated.
// One way to achieve this is it #include the .cpp file with the definition in the header.
template<typename T>
template<int repeat>
void Box<T>::dumpVal()
{
    for (int i = 0; i < repeat; ++i)
    {
        cout << val << endl;
    }
}
```

##### Template specialization

* [Template specialization](https://www.geeksforgeeks.org/template-specialization-c/) refers to specific template definitions for particular data types. Explicit (full) specialization means that all template arguments are provided.

* [Partial specialization](https://en.wikipedia.org/wiki/Partial_template_specialization) means that only some arguments are provided. In C++ partial specialization is not allowed for functions (either member or non-member functions), using overloading is suggested instead.

Template function with full specialization:

```cpp
template<typename T>
void printVector(const vector<T> &vec)
{
    for (int i = 0; i < vec.size(); ++i) { cout << vec[i] << endl; }
}

template<>
void printVector(const vector<string> &vec)
{
    for (int i = 0; i < vec.size(); ++i) { cout << vec[i] << " "; }
}

int main() 
{
    // Strings are separated with spaces instead of newlines.
    printVector<string>({ "ala", "ma", "kota" });
}
```

Template class with full member function specialization:

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }

    void dumpVal();

    T val;
};

template<typename T>
void Box<T>::dumpVal()
{
    cout << val << endl;
}

template<>
void Box<string>::dumpVal()
{
    cout << '\"' << val << '\"' << endl;
}

int main() 
{
    Box<int> box(2); // prints 2
    box.dumpVal();

    Box<string> sbox("ala");
    sbox.dumpVal(); // prints "ala" in quotes
}
```

Template function in a template class with full member function specialization:

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }

    template<typename PT>
    void dumpVal(const PT &prefix);

    T val;
};

template<typename T>
template<typename PT>
void Box<T>::dumpVal(const PT &prefix)
{
    cout << prefix << val << endl;
}

template<>
template<typename PT>
void Box<string>::dumpVal(const PT &prefix)
{
    cout << prefix << '\"' << val << '\"' << endl;
}

// Note: it is not possible to only specialize the member function parameter
// without specializing the class parameter.
template<>
template<>
void Box<string>::dumpVal(const int &prefix)
{
    cout << prefix << ") " << '\"' << val << '\"' << endl;
}

int main() 
{
    Box<string> box("ala");
    box.dumpVal("Val: "); // prints Val: "ala"
    box.dumpVal(1); // prints 1) "ala"
}
```

Template class with partial specialization:

```cpp
template<typename TData, typename TID>
struct VectorBox
{
    VectorBox(const vector<TData> &vecArg, const TID &idArg)
        : vec(vecArg), id(idArg) { }
    void dumpVec() const;
    
    vector<TData> vec;
    TID id;
};

template<typename TData, typename TID>
void VectorBox<TData, TID>::dumpVec() const
{
    cout << id << ": ";
    
    for (int i = 0; i < vec.size(); ++i)
    {
        cout << vec[i] << " ";
    }
}

// Partial specialization: requires specializing the enclosing class.
// It is not possible to partially specialize the function without specializing the class.
template <typename TData>
struct VectorBox<TData, string>
{
    VectorBox(const vector<TData> &vecArg, const string &idArg)
        : vec(vecArg), id(idArg) { }
    void dumpVec() const;
    
    vector<TData> vec;
    string id;
};

template<typename TData>
void VectorBox<TData, string>::dumpVec() const
{
    cout << '\"' << id << '\"' << ": ";
    
    for (int i = 0; i < vec.size(); ++i)
    {
        cout << vec[i] << " ";
    }
}

int main()
{
    VectorBox<int, int> box(vector<int>{ 1, 2, 3 }, 0);
    box.dumpVec();

    VectorBox<int, string> sbox({ 1, 2, 3 }, "ala"); // This id will be enclosed in quotation marks.
    sbox.dumpVec();
}
```

Template class with partial specialization for pointers (again, only allowed for classes):

```cpp
template<typename T>
struct Box
{
    Box(T valArg): val(valArg) { }
    
    void dump()
    {
        cout << val << endl;
    }
    
    T val;
};

template<typename T>
struct Box<T *>
{
    Box(T *valArg): val(valArg) { }
    
    void dump()
    {
        cout << *val << endl;
    }
    
    T *val;
};

int main() 
{
    int n = 5;

    Box<int> box(n);
    box.dump(); // prints 5

    Box<int *> pbox(&n);
    pbox.dump(); // prints 5
}
```

Using `enable_if` for selecting template specialization based on the properties of template arguments.
Various predicates are available from the `<type_traits>` header.

```cpp
template<typename T, typename = typename enable_if<is_arithmetic<T>::value, T>::type>
inline string toString(T val)
{
    return to_string(val);
}

inline string toString(const string &str)
{
    return str;
}

int main()
{
    string str = toString("ala") + toString(5);
    cout << str << endl; // prints ala5
}
```

##### Template metaprogramming

[Template metaprogramming](https://en.wikibooks.org/wiki/C%2B%2B_Programming/Templates/Template_Meta-Programming): performing computation at compile-time with the use of templates. Cumbersome, but Turing-complete, limited use in [real life](https://stackoverflow.com/questions/63494/does-anyone-use-template-metaprogramming-in-real-life).

Example with calculating the factorial using a specialized template for the base case:

```cpp
template<int N>
struct Factorial
{
    enum { value = N * Factorial<N - 1>::value };
};

template<>
struct Factorial<0>
{
    enum { value = 1 };
};

int main()
{
    cout << Factorial<5>::value << endl; // prints 120
    // cout << Factorial<-2>::value << endl; // Wouldn't compile, template instantation max depth exceeded.
}
```

#### Time measurement

Time can be measured using system-specific tools.
Example on Windows using the [query performance counter](https://msdn.microsoft.com/en-us/library/windows/desktop/ms644904%28v=vs.85%29.aspx), requires `Windows.h` header:

```cpp
LARGE_INTEGER start, stop, elapsed;
LARGE_INTEGER frequency;

QueryPerformanceFrequency(&frequency); // ticks per second
QueryPerformanceCounter(&start); // a "high-resolution time stamp"

// Do some work.
for (int i = 0; i < 1000000000; ++i)
    ;

QueryPerformanceCounter(&stop);

// Using QuadPart for 64-bit integers.
elapsed.QuadPart = stop.QuadPart - start.QuadPart;

// Converting to microseconds in order to prevent loss of precision.
elapsed.QuadPart *= 1000000;
elapsed.QuadPart /= frequency.QuadPart;

cout << "Elapsed = " << elapsed.QuadPart << " us" << endl;
```

From C++11, standard header `chrono` can be used.

```cpp
// This measures the CPU time.
// It may advance slower or faster (when more than one core is used) than the wall time.
clock_t start = std::clock();

// Do some work.
for (int i = 0; i < 1000000000; ++i)
    ;

clock_t stop = std::clock();

double elapsedSec = (stop - start) / static_cast<double>(CLOCKS_PER_SEC);
cout << "Elapsed = " << elapsedSec << " s" << endl;
```

```cpp
using namespace chrono;

// This is a clock "with the smallest tick period provided by the implementation", probably wall time.
auto start = high_resolution_clock::now();

// Do some work.
for (int i = 0; i < 1000000000; ++i)
    ;

auto stop = high_resolution_clock::now();
auto elapsed = stop - start;

auto elapsedUs = duration_cast<microseconds>(elapsed).count();
cout << "Elapsed = " << elapsedUs << " us" << endl;
```

#### Variadic functions

A [variadic](http://en.cppreference.com/w/cpp/utility/variadic) function allows for the use of any number of arguments.

```cpp
void printInts(const char *fmt, ...)
{
    va_list args;
    va_start(args, fmt); // 2nd arg to va_start is the name of the last argument before ...

    while (*fmt)
    {
        if (*fmt == 'd') // Int
        {
            int d = va_arg(args, int);
            cout << d << " ";
        }

        fmt += 1;
    }

    va_end(args);
    cout << endl;
}

printInts("ddd", 1, 2, 3); // prints 1 2 3
```

```cpp
void printInts(int count, ...)
{
    va_list args;
    va_start(args, count); // 2nd arg to va_start is the name of the last argument before ...

    for (int i = 0; i < count; ++i)
    {
        int d = va_arg(args, int);
        cout << d << " ";
    }

    va_end(args);
    cout << endl;
}

printInts(3, 1, 2, 3); // prints 1 2 3
```

In C++11 it can be achieved also with a [parameter pack](https://en.cppreference.com/w/cpp/language/parameter_pack) (variadic template):

```cpp
// Functions with parameter packs work like recursion.
template<typename T>
void print(T n) { cout << n << " "; }

// T1 is required for the recursion to finish (it consumes the 1st arg with each call).
template<typename T1, typename ... T2>
void print(T1 arg, T2 ... args)
{
    print(arg);
    print(args...);
}

print(1, 2, 3, "ala"); // prints 1 2 3 ala
```


### Standard Library

[C++ Standard Library](https://en.wikipedia.org/wiki/C%2B%2B_Standard_Library): a collection of classes and functions. Collections do not have thread-safety guarantees for multiple writers.

#### Map

A [map](https://en.cppreference.com/w/cpp/container/map) is a dynamic container of key-value pairs (sorted).
Usually implemented as a red-black tree.
An [unordered_map](https://en.cppreference.com/w/cpp/container/unordered_map) is implemented as a hash table.

* Elements are printed in (key) order:

```cpp
map<string, int> m1 { {"bla", 1}, {"ada", 2}, {"ala", 3} };

for (const pair<string, int> &tup : m1)
{
    cout << tup.first << " " << tup.second << endl; // prints ada 2, ala 3, bla 1
}
```

* Values can be set and accessed with the bracket operator:

```cpp
map<string, int> m1;

m1["bla"] = 1;
m1["ada"] = 2;
m1["ada"] = 3;

cout << m1["bla"] << " " << m1["ada"] << endl; // prints 1 3
```

A custom hash for an unordered map can be provided via a struct with overloaded `operator()` or a lambda.

```cpp
struct Point
{
    Point(int argX, int argY)
        :x(argX), y(argY)
    { }

    // Also needs a defined equality operator in order to be stored in a hash table!
    bool operator==(const Point &other) const
    {
        return this->x == other.x && this->y == other.y;
    }

    int x, y;
};

struct PointHash
{
    size_t operator()(const Point &point) const
    {
        return point.x ^ point.y;
    }
};

int main() 
{
    unordered_map<Point, int, PointHash> map1;
    Point p(2, 2);

    map1[p] = 2;
    cout << map1[p] << endl; // prints 2
}
```

```cpp
auto hashFun = [](const Point &point) { return point.x ^ point.y; };

// Constructor which takes the hash also needs the initial bucket count to be passed.
// Function type can be also defined explicitly as std::function<size_t(const Point &point)>.
unordered_map<Point, int, decltype(hashFun)> map1(1, hashFun);
Point p(2, 2);

map1[p] = 2;
cout << map1[p] << endl; // prints 2
```

#### Set

A [set](https://en.cppreference.com/w/cpp/container/set) is a dynamic container of unique elements.
Usually implemented as a self-balancing BST.
An [unordered_set](https://en.cppreference.com/w/cpp/container/unordered_set) is implemented as a hash table.

* Elements are printed in order:

```cpp
set<int> s1 { 1, 5, 2, 3, 4 };
for (const int n : s1) { cout << n << endl; } // prints 1 2 3 4 5
```

* Element-wise comparison can be achieved with the overloaded equals operator:

```cpp
set<int> s1 { 1, 2, 3, 4, 5 };
set<int> s2 { 1, 2 };

cout << (s1 == s1) << " " << (s2 == s2) << endl; // prints 1 1
cout << (s1 == s2) << " " << (s2 == s1) << endl; // prints 0 0
```

* `insert` inserts a single value or multiple values:

```cpp
set<int> s1 { 1, 2 };

s1.insert(3);
s1.insert(s1.begin(), 4);
s1.insert(s1.end(), 0);

for (const int n : s1) { cout << n << " "; } // prints 0 1 2 3 4
```

```cpp
set<int> s1 { 1, 2 };
set<int> s2 { 3, 4 };

s1.insert(s2.begin(), s2.end());

for (const int n : s1) { cout << n << " "; } // prints 1 2 3 4
```

* Checking whether an element is present:

```cpp
set<int> s1 { 1, 2, 3, 4 };

cout << (s1.count(1) > 0) << " " << (s1.count(5) > 0) << endl; // prints 1 0
cout << (s1.find(1) != s1.end()) << " " << (s1.find(5) != s1.end()) << endl; // prints 1 0
```

#### String

A [string](https://en.cppreference.com/w/cpp/string/basic_string) is a dynamic container for chars which are stored contiguously (i.e. they can be accessed through pointer offset).

* Constructor examples:

```cpp
string str1("ala"); // copy constructor
string str2 = "ala"; // also copy constructor

string str3("ala ma kota", 4, 2); // pos 4, len 2 -> "ma"
string str4("ala ma kota", 3); // len 3 -> "ala"
string str5(5, 'a'); // 5 * 'a' -> "aaaaa"
```

* Comparison can be achieved with the overloaded equals operator:

```cpp
string s11 = "ala";
string s12 = "ala";
string s2 = "kota";

cout << (s11 == s12) << " " << (s12 == s11) << endl; // prints 1 1
cout << (s11 == s2) << " " << (s12 == s2) << endl; // prints 0 0
```

* Append using overloaded `+` and `+=` operators:

```cpp
// Needs string(), otherwise treats these two as const char[].
cout << string("ala") + "ma" << endl; // prints alama

string str = "ala";
str += "ma";

cout << str << endl; // prints alama
```

* Direct access through `c_str()`:

```cpp
string str("ala");
const char *cStr = str.c_str();

for_each(cStr, cStr + str.size(), [](char c) { cout << c; }); // prints ala
```

* `erase`

```cpp
string str = "ala ma kota";
str.erase(4, 3); // pos, len

cout << str << endl; // prints ala kota
```

* `insert` (multiple overloads exist)

```cpp
string str = "ala kota";
str.insert(4, "ma ");

cout << str << endl; // prints ala ma kota
```

* `resize`

```cpp
string str = "ala ma";

str.resize(3);
cout << str << " " << str.size() << endl; // prints ala 3

str.resize(6); // inserts null chars
cout << str << " " << str.size() << endl; // prints ala 6

str.resize(8, 'a');
cout << str << " " << str.size() << endl; // prints alaaa 8
```

* `capacity()`, `size()` (or `length()`), `reserve()` work like for a vector (see below).

#### Vector

A [vector](http://en.cppreference.com/w/cpp/container/vector) is a dynamic container where elements are stored contiguously (i.e. they can be accessed through pointer offset).

* Constructor examples:

```cpp
vector<int> vec1 { 4, 10 }; // Initializer list
for (const int n : vec1) { cout << n << " "; } // prints 4 10

vector<int> vec2(4, 10); // Constructor
for (const int n : vec2) { cout << n << " "; } // prints 10 10 10 10

vector<int> vec3(vec2.begin(), vec2.begin() + 2);
for (const int n : vec3) { cout << n << " "; } // prints 10 10

vector<int> vec4(3);
for (const int n : vec4) { cout << n << " "; } // prints 0 0 0 (3 default-inserted instances)

```

* Direct access through `data() const` (since C++11):

```cpp
vector<int> vec { 1, 2, 3, 4 };

int *p = vec.data();
for_each(p, p + vec.size(), [](int n) { cout << n << " "; }); // prints 1 2 3 4
```

* Element-wise comparison can be achieved with the overloaded equals operator:

```cpp
vector<int> v11 { 1, 2, 3 };
vector<int> v12 { 1, 2, 3 };
vector<int> v2  { 3, 2, 1 };

cout << (v11 == v12) << " " << (v12 == v11) << endl; // prints 1 1
cout << (v11 == v2) << " " << (v12 == v2) << endl; // prints 0 0
```

* `insert` inserts a single value or multiple values:

```cpp
vector<int> vec { 1, 2 };
    
vec.insert(vec.begin(), 3);
vec.insert(vec.end(), 4);

for (const int n : vec) { cout << n << " "; } // prints 3 1 2 4
```

```cpp
vector<int> vec1 { 1, 2 };
vector<int> vec2 { 3, 4 };

vec1.insert(vec1.end(), vec2.begin(), vec2.end());
for (const int n : vec1) { cout << n << " "; } // prints 1 2 3 4
```

* `emplace(const_iterator pos, Args &&... args)` works like insert but constructs the element from args (since C++11):

```cpp
struct A
{
    explicit A(int argN): n(argN) { }
    int n;
};

vector<A> vec;

vec.insert(vec.begin(), A(1));
vec.insert(vec.begin(), A(2));

// Insert wouldn't compile here because the constructor is marked with explicit.
vec.emplace(vec.begin(), 3);

for (const A &a: vec) { cout << a.n << " "; } // prints 3 2 1
```

Using emplace with `move` for performance.

```cpp
vector<string> vec;

string str = "ala";

// Since emplace constructs the object directly from arguments, it is probably better
// to use it here (performance-wise) than push-back which might construct the object twice.
vec.emplace_back(move(str)); // Move leaves str in a "valid but unspecified state".
cout << vec[0] << endl; // prints ala
```

* Searching for an element (checking if present):

```cpp
vector<int> vec { 2, 4, 6, 8 };

cout << (find(vec.begin(), vec.end(), 1) != vec.end()) << endl; // prints 0
cout << (find(vec.begin(), vec.end(), 2) != vec.end()) << endl; // prints 1
```

* `erase` removes a single value or multiple values:

```cpp
vector<int> vec { 1, 2, 3, 4, 5, 6 };

vec.erase(vec.begin());
vec.erase(vec.end() - 1);

for (const int n : vec) { cout << n << " "; } // prints 2 3 4 5

auto it = vec.erase(vec.begin() + 1, vec.begin() + 3);

for (const int n : vec) { cout << n << " "; } // prints 2 5
cout << *it << endl; // Prints 5 - returned iterator follows the last removed element.

vec.clear(); // Removes all elements.
cout << vec.size() << endl; // prints 0
```

* `pop_back()` removes the last element.

* `push_back(const T &val)` adds a copy of val to the end of the vector.

* `rbegin()` and `rend()` return reverse iterators:

```cpp
vector<int> vec1 { 1, 2, 3, 4 };
for (auto it = vec1.rbegin(); it != vec1.rend(); ++it) { cout << *it << endl; } // prints 4 3 2 1
```

* `resize(size_type n, value_type val = value_type())` changes the size and fills with copies of val if new size is larger:

```cpp
vector<int> vec { 1, 2, 3, 4 };

vec.resize(2);
for (const int n : vec) { cout << n << " "; } // prints 1 2

vec.resize(4);
for (const int n : vec) { cout << n << " "; } // prints 1 2 0 0

vec.resize(6, 10);
for (const int n : vec) { cout << n << " "; } // prints 1 2 0 0 10 10
```

* `capacity() const` indicates for how many elements is the space currently allocated.

* `reserve(size_type cap)` increases the capacity to at least `cap` elements.

* `size() const` returns the current element count.


### C++11

Below there are descriptions of most of the C++11 features (this is not exhaustive).
Shorter descriptions are itemized here, longer descriptions are later divided into subsections.

* Use `-std=c++11` switch for compilation.

* `auto n = 5; cout << typeid(n).name() << endl;` prints `i`.

* `constexpr`: a constant value which must be initialized at compile time.

* Enum class values require scoping: `enum class Letters { A, B, C }; cout << static_cast<int>(Letters::A);`, note the use of a static cast (also required to use as switch cases).

* Mark overridden (virtual) functions with `override` keyword.

* `nullptr` is a pointer type NULL (NULL is just 0).

* [Rule of five](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)#Rule_of_Five): destructor, copy constructor, move constructor, copy assignment operator, move assignment operator.

* Static class: `struct Test { Test() = delete; };` (the compiler does not allow any use of any deleted function).

#### Array

```cpp
array<int, 3> tab { 1, 2, 3 };
cout << tab.size() << endl; // prints 3

for (const int i : tab)
{
    cout << i << endl;
}

for_each(tab.begin(), tab.end(), [](int x) { cout << x << endl; });
```

#### Functors

[Functor](https://en.wikipedia.org/wiki/Function_object) = function object.

Using `operator()` (doesn't require C++11):

```cpp
class Add
{
public:
    int operator() (int x, int y, int z = 3) { return x + y; }
};

int main()
{
    Add add;
    cout << "x = " << add(1, 2) << endl;
}
```

Using `std::function`:

```cpp
function<int(int, int)> add = [](int x, int y) { return x + y; };
cout << "x = " << add(1, 2) << endl;
```

Argument binding:

```cpp
auto add = [](int x, int y) { return x + y; };
auto add5 = bind(add, placeholders::_1, 5);

cout << add5(3) << endl; // prints 8
```

Binding a member function:

```cpp
struct Test
{
    void dumpXYZ(int x, int y) const { cout << (x + y + z) << endl; }
    const int z = 5;
};

Test t;
function<void(int, int)> fun = bind(&Test::dumpXYZ, &t, placeholders::_1, placeholders::_2);

fun(1, 2); // prints 8
```

#### Initialization

Using an initializer list for objects:

```cpp
vector<int> vec { 1, 2, 3 };
vector<vector<int>> vec { {1}, {2, 2}, {3} };

map<string, int> m { { "ala", 0 }, { "jarek", 5 } };
tuple<int, int, string> t1 { 2, 1, "ala" };

tuple<int, int> getPair()
{
    return { 0, 5 };
}
```

Initializer list is iterable: 

```cpp
for (const int i : { 1, 2, 3 })
{ 
    cout << i << endl; 
}
```

Uniform initialization (also called brace initialization list, etc.).
This allows for solving the [most vexing parse](https://en.wikipedia.org/wiki/Most_vexing_parse) problem (syntax ambiguity).

```cpp
struct Point
{
    Point()
        :x(0),
         y(0)
         { }

    Point(int argX, int argY)
        :x(argX),
         y(argY)
         { }

    int x, y;
};

Point p1 { 3, 8 };
Point p2 { };
```

Auto deduction:

```cpp
auto n { 2 }; // n is an int
cout << n << " " << typeid(n).name() << endl; // prints 2 i

auto d { 2.5 }; // d is a double
cout << d << " " << typeid(d).name() << endl; // prints 2.5 d

auto f { 2.5f }; // f is a float
cout << f << " " << typeid(f).name() << endl; // prints 2.5 f
```

Initialization for non-static member variables:

```cpp
struct B
{
    B(int xArg): x(xArg) { }
    int x;
};

struct A
{
    B b { 3 };
    int a = 5;
    const static int c = 2; // available before C++11
};

int main()
{
    A a;
    cout << a.b.x << endl; // prints 3
}
```

#### Lambdas

```cpp
sort(tab, tab + n, [](int a, int b) { return a > b; });
```

The return value is automatically deduced. Assigning a lambda to a variable:

```cpp
// Argument parentheses () are optional when there are no args.
auto fun = []() { cout << "lambda" << endl; };
fun(); // prints lambda
```

The return value can be also explicitly specified:

```cpp
int n = 5;
    
// Without "-> int&" returns int and the following assignment fails.
auto f = [](int &n) -> int& { return n; };

f(n) = 10;
cout << n << endl; // prints 10
```

Lambdas automatically capture constants, in addition: `[x]` captures `x` by value, `[&x]` captures x by reference.

* `transform(tab, tab + n, tab, [&z](int x) { return x + z; });` works like map.
* `for_each(tab, tab + n, [&z](int &x) { x = x + z; });` also works like map (the same).
* `int acc = 0; for_each(tab, tab + n, [&acc](int x) { acc = acc + x; });` works like reduce.

Removing elements (filtering):

* Removing elements from a vector using iterators (no lambda):

```cpp
for (auto it = vec.begin(); it != vec.end(); )
{
    if (*it % 2 != 0)
    {
        it = vec.erase(it);
    }
    else
    {
        ++it;
    }
}
```

* Removing elements from a vector like filter with a lambda:

```cpp
vector<int> filtered;
for_each(vec.begin(), vec.end(), [&filtered](int x) { if (x % 2 == 0) { filtered.push_back(x); } });
```

#### Move semantics

* **lvalue**: has address and can be assigned.

* **rvalue**: a temporary object `string getName() { return "ala"; } string &&name = getName();`

* obtaining an rvalue explicitly: `string s = "ala"; string &&sRef = move(s);`

An example with a rule of five implementation follows.

```cpp
class MyString
{
public:
    // No argument constructor.
    MyString() { }
    
    // Destructor
    ~MyString()
    {
        delete[] buf;
    }

    // Argument constructor.
    MyString(const string &str)
    {
        this->size = str.size();
        this->buf = new char[size + 1];

        strcpy(buf, str.c_str());
    }

    // Copy constructor.
    MyString(const MyString &other)
    {
        this->size = other.size;
        this->buf = new char[size + 1];

        strcpy(buf, other.buf);
    }

    // Move copy constructor.
    MyString(MyString &&other)
    {
        this->size = other.size;
        this->buf = other.buf;

        // Prevents the destructor from freeing the "stolen" memory.
        other.buf = nullptr;
    }

    // Copy assignment operator using copy-and-swap idiom (for both lvalues and rvalues).
    // This is ambiguous to the compiler if used together with the move operator,
    // so we use the version with reference as an argument (below).

    // MyString &operator= (MyString other)
    // {
    //     swap(this->size, other.size);
    //     swap(this->buf, other.buf);

    //     return *this;
    // }
    MyString &operator= (const MyString &other)
    {
        delete[] buf;

        this->size = other.size;
        this->buf = new char[size + 1];

        strcpy(buf, other.buf);

        return *this;
    }

    // Move copy assignment operator.
    MyString &operator= (MyString &&other)
    {
        if (this != &other)
        {
            delete[] buf;

            this->size = other.size;
            this->buf = other.buf;

            // Prevents the destructor from freeing the "stolen" memory.
            other.buf = nullptr;
        }

        return *this;
    }

    inline const char *getBuf() const { return buf; }

private:
    size_t size = 0;
    char *buf = nullptr;
};

int main()
{
    MyString s1("ada");
    MyString s2("ala");
    
    MyString s3 = s2; // copy constructor
    s2 = s1; // copy assignment operator

    cout << s2.getBuf() << " " << s3.getBuf() << endl; // prints ada ala

    s3 = move(s1); // move copy assignment operator
    MyString s4 = move(s2); // move copy constructor

    cout << s3.getBuf() << " " << s4.getBuf() << endl; // prints ada ada
}
```

#### Multithreading

Before C++11 it was required to use OS-specific functionality, e.g., pthreads on Linux. In C++11 it is possible to use a unified interface for multithreading.
Compile with `-pthread` on Linux.

* Launching a simple thread:

```cpp
thread t1([]() { cout << "t1" << endl; });
t1.join(); // Blocks until t1 finishes
```

* **Atomic access**:

```cpp
vector<thread> threads;

atomic<int> n;
n = 0;

for (int i = 0; i < 1000; ++i)
{
    threads.push_back(thread([&n]() {
        n += 1;
    }));
}
```

* **Call once**:

```cpp
vector<thread> threads;

once_flag flag1;
auto once = [&flag1]() { call_once(flag1, []() { cout << "Called!" << endl; }); };

for (int i = 0; i < 5; ++i)
{
    threads.push_back(thread(once));
} // Will print "Called!" only once.
```

* Threads with **synchronization**:

```cpp
vector<thread> threads;
mutex mut;

for (int i = 0; i < 5; ++i)
{
    threads.push_back(thread([i, &mut]() {
        mut.lock();
        cout << "t: " << i << endl;
        mut.unlock();
    }));
}
```

```cpp
vector<thread> threads;
mutex mut;

for (int i = 0; i < 5; ++i)
{
    threads.push_back(thread([&mut]() {
        lock_guard<mutex> guard(mut); // or use unique_lock which has more flexibility
        cout << this_thread::get_id() << endl;
    }));
}
```

* Thread with a **timed mutex** (i.e. mutex with a timeout):

```cpp
int main()
{
    vector<thread> threads;
    timed_mutex mut;

    mut.lock();

    threads.push_back(thread([&mut]() {
        cout << "Locking..." << endl;
        bool res = mut.try_lock_for(chrono::seconds(1));

        // This will print 0 (false) because we fail to acquire the lock.
        cout << "After locking, res = " << res << endl;
    }));

    threads[0].join();
}
```

* Threads with **blocking** on the result:

```cpp
vector<future<int>> res;

for (int i = 0; i < 5; ++i)
{
    res.push_back(async(launch::async, [i]() { // or launch::deferred for lazy eval
        this_thread::sleep_for(chrono::seconds(3));
        return i;
    }));
}

for (auto &f : res) { cout << f.get() << endl; }
```

* Threads with a **condition variable**:

```cpp

```

* `future<void> res(async(fun));`: async can take fun with args or a lambda, `res.get();` blocks until the result is available.
* `std::promise` is the producer and `std::future` is the consumer.


#### Range-based for loop

Simple example: `for (const int i : tab) { }`. It works for static arrays and containers with `begin()` and `end()` (string, vector, etc.).

Custom-implemented range which works with the range-based loop:

```cpp
class Range
{
public:
    class iterator
    {
        public:
            iterator(int start)
                :i(start) { }

            friend bool operator== (const iterator &i1, const iterator &i2)
            {
                return i1.i == i2.i;
            }
            friend bool operator!= (const iterator &i1, const iterator &i2)
            {
                return !(i1 == i2);
            }

            int &operator* ()
            {
                return i;
            }
            int &operator++ ()
            {
                return ++i;
            }

        private:
            int i;
    };

    Range(int startArg, int endArg)
        :startVal(startArg), endVal(endArg) { }

    iterator begin() { return iterator(startVal); }
    iterator end() { return iterator(endVal + 1); };

private:
    int startVal, endVal;
};

for (int n : Range(1, 6))
{
    cout << n << endl;
}
```

#### Smart pointers

* **Shared pointer**: `shared_ptr<int>tab (new int[size]);`. Resource is deallocated when the last pointer is destroyed. Thread-safe for reference counting, not thread-safe for pointed object access.

Shared pointer can be created using the `make_shared` function:

```cpp
struct Test { int a; };
auto ptr = make_shared<Test>(); // ptr is a shared_ptr<Test>
cout << ptr->a << endl;
```

* **Unique pointer**: `unique_ptr`. Only one reference, cannot be copied, move semantics allow for ownership transfer.

* **Weak pointer**: `weak_ptr`. Doesn't increase the count, useful for preventing circular dependencies.

#### Static assert

Static assert can be used for checks at compile time.

```cpp
struct B
{
    int x = 2;
};

const int k = 2;
// Works only with constant expressions.
static_assert(k > 1, "k must be greater than 1");

// Objects need to be constexpr.
constexpr B b;
static_assert(b.x > 1, "x must be greater than 1");
```

#### Tuple

Creating a heterogeneous tuple:

```cpp
tuple<int, string> tup1 = make_tuple(1, "ala");
cout << get<0>(tup1) << " " << get<1>(tup1) << endl;
```

Using `tie` in order to unpack a tuple:

```cpp
int x, y;
tie(x, y) = make_tuple(1, 2);

cout << x << " " << y << endl; // prints 1 2
```

Using `tie` with a function returning multiple values:

```cpp
random_device rd;
mt19937 mt(rd());
uniform_int_distribution<int> dist(1, 100);

auto rand3 = [&mt, &dist]() { return make_tuple(dist(mt), dist(mt), dist(mt)); };

int x, y, z;
tie(x, y, z) = rand3();

cout << x << " " << y << " " << z << endl; // prints x y z
```

#### Using

Keyword `using` can be used as a `typedef`:

```cpp
using id = unsigned long; // This is equivalent to: typedef unsigned long id;

id n = 100;
cout << n << endl; // prints 100
```


### C++14

Below there are descriptions of most of the C++14 features (this is not exhaustive).
Shorter descriptions are itemized here, longer descriptions are later divided into subsections.

* Use `-std=c++14` switch for compilation.

* Binary literals: `cout << 0b10001 << endl` prints 17.

* Decimal separator: `cout << 10'000.0 << endl` prints 10000.

* Added a `make_unique` function for unique pointer construction.

#### Chrono literals

Chrono duration from C++11 augmented with literals:

```cpp
auto day = 24h; // same as chrono::hours(24)
auto min = 2min; // same as chrono::minutes(2);

cout << day.count() << endl; // prints 24
cout << min.count() << endl; // prints 2

auto diff = day - min;
cout << diff.count() << endl; // prints 1438 (1440 minutes in a day minus 2)

auto millisInTwoMinutes = chrono::milliseconds(min);
cout << millisInTwoMinutes.count() << endl; // prints 120000
```

#### Deduced return type

```cpp
// This can be added in order to cause a compiler warning when the function is called.
[[deprecated("legacy system")]]
auto add(int x, int y) { return x + y; }

int main()
{
    cout << add(5, 4) << endl; // prints 9
}
```

#### Improved lambdas 

**Generics** can be achieved in lambdas using `auto` keyword:

```cpp
auto add = [](auto x, auto y) { return x + y; };
 
cout << add(2, 4) << endl; // prints 6
cout << add(string("ala"), string("kota")) << endl; // prints alakota
```

Returning a reference to `auto`:

```cpp
auto add = [](auto &x, auto &y) { x += y; return x; }; // Returns a copy.

int x = 1, y = 2;
int ret = add(x, y);

cout << ret << " " << x << endl; // prints 3 3

ret += 2;
cout << ret << " " << x << endl; // prints 5 3 (x is unchanged)

auto addRef = [](auto &x, auto &y) -> auto &{ x += y; return x; }; // Returns a reference.

x = 1;
y = 2;
int &ref = addRef(x, y);

cout << ref << " " << x << endl; // prints 3 3

ref += 2;
cout << ref << " " << x << endl; // prints 5 5 (x is changed)
```

Lambdas with **capture initializers**:

```cpp
// Variable n has an initial value = 0, it is retained through calls and local to the lambda.
// Keyword mutable allows for the modification of a variable which is captured by value.
auto add = [n = 0](auto x) mutable { n += x; return n; };

cout << add(2) << endl; // prints 2
cout << add(2) << endl; // prints 4
cout << add(2) << endl; // prints 6
```

```cpp
vector<int> vec { 1, 2, 3, 4 };
auto reduceMult = [acc = 1](auto x) mutable { acc *= x; return acc; };

int cur;
for (const int n : vec) { cur = reduceMult(n); }
cout << cur << endl; // prints 24
```

#### Variable templates

```cpp
template<class T> // Must be outside block scope.
constexpr T pi = T(3.1415926535897932385L); 

int main()
{
    cout << pi<double> << endl; // prints 3.14...
    cout << pi<float> << endl; // prints 3.14...
    cout << pi<int> << endl; // prints 3
}
```

### C++17 

Below there are descriptions of most of the C++17 features (this is not exhaustive).

* Use `-std=c++17` switch for compilation.

#### Filesystem

Compile with `-lstdc++fs` option.

```cpp
filesystem::path f1 = "test.txt";

cout << filesystem::exists(f1) << endl; // prints 0
cout << f1.filename() << " " << f1.extension() << endl; // prints "test.txt" ".txt" (both in quotes)

ofstream(f1.filename()) << "koty";

// Prints 4. Throws an exception if the file is not present.
cout << filesystem::file_size(f1) << endl;
```

#### Folding for parameter packs

This offers a simplified syntax when compared to C++11.

```cpp
template<typename... T>
auto sum(T... args)
{
    return (... + args);
}

template<typename... T>
auto sumSeeded(T... args)
{
    return (10 + ... + args);
}

// Types can be mixed. Prints 60.75.
cout << sum(10, 20.5f, 30.25) << endl;
// Types can be mixed. Prints 70.75 (60.75 + 10).
cout << sumSeeded(10, 20.5f, 30.25) << endl;
```

#### Nested namespaces

`namespace A::B::C { }` is equivalent to `namespace A { namespace B { namespace C { } } }`.
Example usage:

```cpp
namespace A::B::C // nested namespace
{
    int a = 1;
}

namespace A
{
    namespace B
    {
        namespace C
        {
            int b = 2;
        }
    }
}

int main()
{
    cout << A::B::C::a << " " << A::B::C::b << endl; // prints 1 2
}
```

#### Optional

```cpp

```

#### Unpacking tuples

```cpp
pair<string, int> p1 { "ala", 2 };
    
// This is similar to tie(name, count) = p1, which requires previous variable declaration.
auto [name, count] = p1;
cout << name << endl; // prints "ala"
cout << count << " " << typeid(count).name() << endl; // prints 2 i
```

### Makefile

```makefile
# First macros are provided. These can be uncommented with '#' if needed.
CC        = g++                        # Compiler name.
CCFLAGS   = -Wall -pedantic -std=c++11 # Compiler flags: all warnings, pedantic, C++11 standard.
OPTFLAGS  = -DNDEBUG -O3               # Optional flags: define NDEBUG (disables assert()), opti level 3.

INCLUDE   = -I"/path/to/lib"           # -I: add directory searched for header files.
LDFLAGS   = -L"/path/to/lib"           # -L: add directory searched for -l.

# Link with the library libm.a (static) or libm.so (shared, dynamic).
# Add -static to LDFLAGS to prefer static to dynamic linking (i.e. search for .a files first).
LDLIBS    = -lm

EXE       = sopang                     # Executable name
OBJ       = main.o sopang.o            # List of object files

# Default rule is all.
all: $(EXE)

# The executable depends on all object files. $@ is the target name, $^ are the dependencies.
# Note that LDLIBS come at the end because the linker should encounter undefined symbols first
# (i.e. before the libraries).
$(EXE): $(OBJ)
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(LDFLAGS) $^ -o $@ $(LDLIBS)

# Object file main.o depends on the following .cpp and .hpp files.
# -c means stop after the compilation (no linking), this produces the object file main.o.
main.o: main.cpp helpers.hpp params.hpp sopang.hpp
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(INCLUDE) -c main.cpp

sopang.o: sopang.cpp sopang.hpp helpers.hpp
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(INCLUDE) -c sopang.cpp

.PHONY: clean # Phony targets are not associated with file dependencies.

# This is invoked when the user types "make clean".
# The following command removes the executable and object files.
clean:
	rm -f $(EXE) $(OBJ)

rebuild: clean all
```


Python
--------------------

[Python](https://en.wikipedia.org/wiki/Python_(programming_language)): interpreted, object-oriented, garbage-collected, with name binding, duck typing (based on runtime object interface), has multiple libraries. Reference interpreter is called CPython, other: PyPy which is based on JIT.
The description below refers to **Python2** which is not compatible with Python3.

Python is [not great](https://stackoverflow.com/questions/1017621/why-isnt-python-very-good-for-functional-programming) for functional programming:

* no tail recursion (i.e. no using equivalent memory to a loop)
* no pattern matching
* no concise way to combine functions
* not too many list functions


### Selected features

* `[1,2,3] == [1,2] + [3]`

* `[1,2,3,4][1 : 3] == [2,3]`, `[1,2,3][ : 1] == [1]`

* `[1,2,3,4][::2] == [1,3]`, `[1,2,3][::-1] == list(reversed([1,2,3]))`

* `l = [[]] * 5`: same list reference is replicated, doesn't work as expected (adding an element to one sublist will add it to all sublists). Use `l = [[] for _ in xrange(5)]` instead.

* Deep copy: `l = copy.deepcopy(x)`, works with nested lists.

* `dir(obj)` returns a list of defined members (functions and variables).

* `for i, s in enumerate(["ala", "ma", "kota"]): print i, s` prints `0 ala 1 ma 2 kota`

* `"{0} {1:.2f}".format(0.6666, 0.6666)` returns `0.6666 0.67`

* Functions are first-class citizens in Python: nested functions are allowed, functions can be assigned, returned, etc.

* `globals()` and `locals()` return a dictionary of global/local variables. They can be used for reflection.

* Import from a subdirectory requires a present `__init__.py` file (may be empty) in this subdirectory.

* `reverse(l)` returns an iterator to `l` (if `l` changes, data pointed to by an iterator changes too).

* Serialization (translating data to storage/transmission format) can be realized using `pickle` or `cPickle` (the latter is faster).

* Tertiary operator: `x = 2 if len(s) > 5 else 10`

* Tuple `(1,2,3)` is immutable.

* `with` works like try/finally, requires context management protocol: `__enter__()`, `__exit()__`.

* `xrange` and `range` start from 0, Python2: `xrange` is a generator and `range` creates a list, in Python3 there is only `range` which is a generator.

* `zip([1,2,3],[4,5,6]) == [(1,4), (2,5), (3,6)]`


### Functions

#### Running main

```python
def main():
    print "Started"

# This is executed if our script is run as the main program.
if __name__ == "__main__":
    main()
```

#### Calling with args

```python
def add(x, y):
  return x + y

def add3(x, y = 3):
  return x + y

def addStar(*args): # All params as a tuple
  return sum(args)
```

* `print addStar(1, 2, 3)`
* Default arg values must follow from the left.
* Calling with explicit arg names: `print add(x = 5, y = 4)`.
* Partial application (argument binding): `add5 = functools.partial(lambda x,y: x + y, 5)`
* Unpacking operator: `print add(*[1, 2])`

#### Keyword args

```python
def addKwargs(**kwargs): # All keyword params as a dict
  return sum(kwargs.values())
```

* `print addKwargs(x = 2, y = 3)`
* `print addKwargs(**{"x": 2, "y" = 3})`


### Classes

```python
class Point(object):
  n = 5 # Static var, access as Point.n

  def __init__(self, x, y):
    self.x = x
    self.y = y

  def mysum(self): # Not passing self would mean a static function.
    return self.x + self.y
```

* Always inherit from `object` for access to class names (new-style classes).
* Convention for private: `self._x`, private with a mangled name: `self.__x` (works for both functions and variables).
* Dictionary containing all member variables: `print p1.__dict__`
* Extend objects: `p1.z = 8`, now `print p1.z` works (only if z was set for this object).

#### Inheritance

```python
class Point3D(Point):
  def __init__(self, x, y, z):
    Point.__init__(self, x, y)
    self.z = z

  def mysum(self):
    return Point.mysum(self) + self.z
```


### File system

Python provides convenient abstractions for working with the file system.
Selected examples are presented below.

Obtaining the list of all files with a given extension from a directory:

```python
dirPath = "."
ext = ".py"

print [path for path in os.listdir(dirPath) if os.path.splitext(path)[1] == ext]
```

Creating a file in a directory if it doesn't yet exist:

```python
dirPath = "."
fName = "test.txt"

fPath = os.path.join(dirPath, fName)

if not os.path.exists(fPath):
    open(fPath, "w")
```

Reading a numerical csv file:

```python
fPath = "test.csv"

# The file will be closed at the end of the "with" block.
with open(fPath, "r") as f:
    text = f.read()

lines = text.split("\n")
data = [[float(num) for num in l.split(",") if num] for l in lines if l]
```

Returning the sum of file sizes from a directory (recursive, includes subdirectories),
ignoring Linux hidden folders:

```python
# Expands the home directory.
dirPath = os.path.expanduser("~/Desktop/test")
fSizes = []

for dirPath, _, fileNames in os.walk(dirPath):
    # We exclude paths which are contained within a hidden directory.
    if "." not in dirPath:
        for fName in fileNames:
            fSizes += [os.path.getsize(os.path.join(dirPath, fName))]

print sum(fSizes) / 1024.0
```


### Filter, map, reduce

* List comprehension combines map with filter: `[2 * x for x in xrange(10) if x % 2 == 0]`.
* `map(lambda x: 2 * x, filter(lambda x: x % 2 == 0, xrange(10)))`: this is the same as list comprehension above.
* `map(len, ["ala","ma","kota"]) == [3,2,4]`
* `sum([1,2,3]) == reduce(lambda x,y: x + y, [1,2,3], 0)`


### List functions

* `del l[1]` removes an element at index 1.
* `del l[:]` clears the entire list.
* `l.pop(1)` removes an element at index 1 and returns this element.
* `l.pop(l.index(max(l)))` removes the max element.
* `l.remove(x)` removes the first value matching `x`.


### Multithreading

Note that in CPython there can only be a [single thread](https://docs.python.org/2/library/threading.html) running, due to [global interpreter lock](https://en.wikipedia.org/wiki/Global_interpreter_lock).
For this reason, multithreading in Python is useful for I/O-bound tasks, but not for CPU-bound tasks (use libraries or multiprocessing module for the latter).

Simple threads with locks:

```python
n = 0
lock = threading.Lock()

def fun():
    print "Started: " + threading.current_thread().name
    global n

    for _ in xrange(100000):
        with lock:
            n += 1

threads = []

for i in xrange(4):
    threads += [threading.Thread(target = fun)]

for t in threads:
    t.start()
for t in threads:
    t.join()

# Prints 400000.
# Without join, prints 0 or some small value.
# Without a lock, prints some value <= 400000.
print "n = {0}".format(n)
```

Example using the `joblib` library. Each function instance is executed in parallel and separately.

```python
from joblib import Parallel, delayed

def fun(i):
    n = 0

    for _ in xrange(1000000):
        n += 1

    return n + i

res = Parallel(n_jobs = 4)(delayed(fun)(i) for i in xrange(4))
print res # prints [1000000, 1000001, 1000002, 1000003]
```


### Plotting

```python
import matplotlib.pyplot as plt

plt.title("title")
plt.xlabel("X")
plt.ylabel("Y")

plt.tight_layout()
plt.xlim(0.9, 3.1)
plt.ylim(3.9, 6.1)

# Draws a black line with dots.
plt.plot([1,2,3], [4,5,6], "ko-")
plt.show()
```


### Time measurement

```python
import time

# Time since epoch in seconds, precision is platform-dependent.
# Alternative: time.clock() which measures CPU time on Unix and QueryPerformanceCounter on Windows.
start = time.time()

for i in xrange(100000000):
    pass

stop = time.time()

elapsed = stop - start
print "Elapsed = {0} s".format(elapsed)
```


Git
--------------------

#### [Basic commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)

* `git init`

* `git clone [address]`
</br>

* `git add -u` – add all already-tracked files

* `git add .` – add all files from the current directory including untracked files

* `git blame [file]` – show who and when changed each line of `[file]`

* `git checkout [branch-name]` – switch to branch `[branch-name]`

* `git checkout -b [branch-name] [base-branch-name]` – create a branch `[branch-name]` out of `[base-branch-name]`

* `git checkout -- [file]` – discard local changes in `[file]` (`--` means that what follows are not command line flags, which makes it work even if the file is named like some git flag)

* `git commit -a` – commits changes to all tracked files (not only in the current directory)

* `git commit -m "[msg]"` – commit with message `[msg]`

* `git commit --amend -m "[msg]"` – change the last commit message to `[msg]` (changing the remote branch requires force pushing)

* `git diff [file]` – show unstaged changes for `[file]`, `git diff --staged` to show all staged changes, `git diff --staged [file]` to show all staged changes for `[file]`

* `git log` – show all commits starting from the latest one, `git log -p` to show changes alongside, `git log origin/master..master` to show all commits which are not pushed (all in between `origin/master` and `master`)

* `git merge [branch-name]` – merge current branch with branch `[branch-name]`

* `git pull` (this is `git fetch` followed by `git merge` to the current local branch)

* `git push` – push local to to the corresponding remote branch

* `git push origin [branch-name]` – push only branch `[branch-name]`

* `git rebase [branch-name]` – moves the entire current branch to the tip of `[branch-name]`

* `git reset --hard origin/master` – remove all local changes

* `git reset [file]` – remove `[file]` from the current index, this is basically undo for `git add [file]`

* `git show [commit id]` – show log and changes from commit with id `[commit id]`

* `git show [commit id]:./main.cpp` – show file `main.cpp` from a commit with id `[commit id]`

* `git rm [file]` – remove `[file]`

* `git rm --cached [file]` – stop `[file]` from being tracked

#### Related terminology

* [Origin](https://stackoverflow.com/questions/9529497/what-is-origin-in-git): local alias for a remote repository (`git remote show origin` to query).
* [Pull request](https://yangsu.github.io/pull-request-tutorial/): request that a maintainer (somebody in the authority) pull the changes and merge them after approval (i.e. add them into the codebase).
* [Submodule](https://git-scm.com/docs/git-submodule): another repository embedded as part of a current repository.

#### GitFlow

[GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) is a workflow model based on branches.

* **master** branch: releases with version numbers (main branch number 1)
* **develop** branch: integration branch for features (main branch number 2)
<br />

* **feature**: branched out of and into develop, single feature = single branch
* **hotfix**: quick patches, the only branch out of master, merged both with master and develop/release
* **release**: branched out of develop, no new features can be added, merged into master when ready to ship, next also merged back into develop

This is in opposition to a [centralized](https://www.atlassian.com/git/tutorials/comparing-workflows) (SVN-like) workflow, where all features are branched out of and merged into a single master branch.

Acknowledgements
--------------------

All references are provided as clickable links next to the descriptions.
These are mostly based on [Wikipedia](https://en.wikipedia.org/wiki/Main_Page) and the [C++ reference](http://en.cppreference.com/w/) website.
