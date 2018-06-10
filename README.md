Table of Contents
--------------------

1. [Table of Contents](#table-of-contents)
1. [General](#general)
    * [Basic math](#basic-math)
    * [Complexity](#complexity)
        * [Amortized analysis](#amortized-analysis)
    * [Graphs](#graphs)
    * [Data structures](#data-structures)
        * [Basic](#basic)
            * [BST](#bst)
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
    * [Principles](#principles)
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
        * [Memory management](#memory-management)
        * [Operator overloading](#operator-overloading)
        * [Preprocessor directives](#preprocessor-directives)
        * [Templates](#templates)
            * [Template specialization](#template-specialization)
        * [Variadic functions](#variadic-functions)
    * [Standard Library](#standard-library)
        * [String](#string)
        * [Vector](#vector)
    * [C++11](#c11)
        * [Array](#array)
        * [Functors](#functors)
        * [Lambdas](#lambdas)
        * [Move semantics](#move-semantics)
        * [Multithreading](#multithreading)
        * [Smart pointers](#smart-pointers)
        * [Tuple](#tuple)
    * [C++14](#c14)
    * [C++17](#c17)
    * [Makefile](#makefile)
1. [Python](#python)
    * [Selected features](#selected-features)
    * [List functions](#list-functions)
    * [Functions](#functions)
    * [Calling with args](#calling-with-args)
    * [Keyword args](#keyword-args)
    * [Filter, map, reduce](#filter-map-reduce)
    * [Classes](#classes)
    * [Inheritance](#inheritance)
    * [Plotting](#plotting)
1. [Git](#git)
    * [Basic commands](#basic-commands)
    * [Related terminology](#related-terminology)
    * [GitFlow](#gitflow)

General
--------------------

### Basic math

* [Arithmetic series](https://en.wikipedia.org/wiki/Arithmetic_progression) sum: n(a1 + an) / 2 = ϴ(n²)

* [Bayes theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem): P(A|B) = P(B|A) P(A) / P(B)

* [Binomial coefficient](https://en.wikipedia.org/wiki/Binomial_coefficient) (ways to select unordered items): n! / [k! (n - k)!], for ordered items: n! / (n - k)!

* [Harmonic series](https://en.wikipedia.org/wiki/Harmonic_series_(mathematics)) sum: 1 + 1/2 + 1/3 + ... + 1/n = ln n + O(1)

* There are n! [permutations](https://en.wikipedia.org/wiki/Permutation) for n elements: n ways to choose the 1st element, n-1 ways to choose the 2nd element, etc. k-permutation = permutation of subsequence of length k.


### Complexity

* o, O, ϴ, Ω, ω
* O(1) < O(log n) < O(n) < O(n log n) < O(n<sup>2</sup>) < O(2<sup>n</sup>) < O(n!)
* P, NP, NP-complete, NP-hard, [P vs NP](https://en.wikipedia.org/wiki/P_versus_NP_problem)

#### Amortized analysis

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

Average cases are presented. BST is assumed to be balanced, hashing a simple item is assumed to be constant-time.
For the hash table worst-case for all operations is O(n).

Structure  | Access   | Search   | Insert/delete  | Space
---------- | -------- | ---------| -------------- | -------
Array      | O(1)     | O(n)     | O(n)           | O(n)
List       | O(n)     | O(n)     | O(1)           | O(n)
BST        | O(log n) | O(log n) | O(log n)       | O(n)
Hash table | O(1)     | O(1)     | O(1)           | O(n)

##### BST

* [AVL](https://en.wikipedia.org/wiki/AVL_tree): first self-balancing BST. Height of two child subtrees differs by at most 1. In order to balance after a regular insertion of new node w: travel up to the root to find the first unbalanced node z. Rotate subtree rooted with z: 4 cases based on node z and its child/grandchild: a) y is left, x is left (on the path to w), b) left-right, c) right-left, d) right-right.

* [Red-black](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree): each node is R or B, the root is B. If node is R, both children are B. Any path from node to any leaf (NIL, B) has the same number of black nodes.

* [Treap](https://en.wikipedia.org/wiki/Treap): BST with priorities maintained in a heap. Searching is just like BST, insertion: generate random priority, add leaf at a regular position, use rotations in order to restore the max-heap property.

##### Heap

[Heap](https://en.wikipedia.org/wiki/Heap_(data_structure)): priority queue, max-heap or min-heap. Adding: add at the bottom, continue swapping with parent (sifting up). Deleting: swap root with the last leaf, sift down the new root. Various kinds of heaps exist: Brodal, Fibonacci, etc.

#### String matching

* [Trie](https://en.wikipedia.org/wiki/Trie): a tree in which the position of a node describes the associated value, search is proportional to the pattern length, that is O(m).

* [Suffix array](https://en.wikipedia.org/wiki/Suffix_array): stores indexes of sorted suffixes from the input text, search is O(m log n), space is around 5n.

* [Suffix tree](https://en.wikipedia.org/wiki/Suffix_tree): a trie which stores all suffixes of the input string, search is O(m), space is around 10n.


### Algorithms

* [Brute-force](https://en.wikipedia.org/wiki/Brute-force_search): exhaustive search, checking all solution candidates.

* [Dynamic programming](https://en.wikipedia.org/wiki/Dynamic_programming): solving simpler subproblems and storing solutions, e.g., Fibonacci sequence with [memoization](https://en.wikipedia.org/wiki/Memoization) (result caching).

* [Greedy algorithm](https://en.wikipedia.org/wiki/Greedy_algorithm): makes a locally optimal choice at each step.

* [Las Vegas](https://en.wikipedia.org/wiki/Las_Vegas_algorithm) vs [Monte Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_algorithm): LV is a randomized algorithm which always produces a correct result or informs about the failure (it gambles with computational resources), MC is a randomized algorithm which might report an incorrect result (it gambles with result accuracy).

#### Graphs

* [A*](https://en.wikipedia.org/wiki/A*_search_algorithm): maintain a closed and open set (open has start at the begginning). While open is not empty, take current from open with lowest estimate, move it to closed, and expand all negibhors. Finish if current is the goal. Heuristic must be admissible (not overestimating).

* [B*](https://en.wikipedia.org/wiki/B*)

* [D*](https://en.wikipedia.org/wiki/D*)

* [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm): specific case of A* without a heuristic.

* [Coloring](https://en.wikipedia.org/wiki/Graph_coloring): labeling where no adjacent vertexes share a label.

* [TSP](https://en.wikipedia.org/wiki/Travelling_salesman_problem): find the shortest Hamiltonian cycle (visits each node exactly once and returns to the start).

* [Voronoi diagram](https://en.wikipedia.org/wiki/Voronoi_diagram): partitioning into regions based on a distance to the closest point.

#### Machine learning

Supervised, unsupervised, reinforced.
Applications:

* [Classification](https://en.wikipedia.org/wiki/Statistical_classification) (discrete)
* [Regression](https://en.wikipedia.org/wiki/Regression_analysis) (continuous)
* [Clustering](https://en.wikipedia.org/wiki/Cluster_analysis)
* [Density estimation](https://en.wikipedia.org/wiki/Density_estimation)

Techniques:

* [ANN](https://en.wikipedia.org/wiki/Artificial_neural_network)
* [Association rules](https://en.wikipedia.org/wiki/Association_rule_learning): created mostly based on frequency of appearance, e.g., `{onions, potatoes} => {burger}`.
* Bayesian
* [Decision tree](https://en.wikipedia.org/wiki/Decision_tree_learning): sets of rules
* [Deep learning](https://en.wikipedia.org/wiki/Deep_learning): using multiple layers of nonlinear processing units. Levels correspond to different levels of abstraction and form a hierarchy of concepts.
* [SVM](https://en.wikipedia.org/wiki/Support_vector_machine): separate data by hyperplanes with the largest margin. Kernel functions allow for implicit mapping into higher dimensions in order to ensure data segregation.

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

* [Needleman-Wunsch](https://en.wikipedia.org/wiki/Needleman%E2%80%93Wunsch_algorithm)

* [Smith-Waterman](https://en.wikipedia.org/wiki/Smith%E2%80%93Waterman_algorithm)

#### Trees

* [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm): minimum spanning tree. Divide all nodes into a forest, always take the shortest edge, span only if spanning two distinct trees, otherwise discard.

* [Traversal](https://en.wikipedia.org/wiki/Tree_traversal): DFS (pre-order, in-order, post-order), BFS (use a priority queue based on depth).


### Design patterns

The following summary is based on [Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern) page. Obvious patterns are only listed and not described.

#### Creational

* Abstract factory: encapsulate individual factories under a generic interface.

* Builder: separate construction from interpretation.

* Dependency injection

* Factory

* Lazy initialization

* Multiton: registry of singletons

* Object pool

* Prototype: create new objects from a skeleton.

* RAII: constructor/destructor

* Singleton

#### Structural

* Adapter: wrapper

* Bridge: decouple abstraction from implementation in order to facilitate changes.

* Composite: groups of objects treated the same as a single object.

* Decorator: dynamically add behavior to an individual object, without affecting the behavior of other objects (i.e. alter behavior at runtime).

* Extension: allows for adding new functionality to a class without inheritance (e.g., extension functions in Kotlin).

* Facade: a higher-level interface which is easier to use.

* Flyweight: use sharing to support large numbers of lightweight similar objects efficiently.

* Marker: use an empty interface to indicate specific behavior (e.g., Serializable).

* Proxy: used in order to control access to an object.

* Twin: multiple inheritance in languages that do not support it (two closely coupled subclasses, each derived from one superclass).

#### Behavioral

* Blackboard: knowledge sources publish potential solutions on the blackboard, the control component is in between.

* Chain of responsibility: a chain of processing objects receives the commands which are handled or passed along. Essentially if..elif..else which can be dynamically reconfigured.

* Command: object encapsulates all information needed to perform an action at a later time, including the receiver.

* Interpreter: use of DSL, e.g., SQL, user interface descriptions.

* Iterator: decouples algorithms from containers.

* Mediator: encapsulates communication between objects, reduces coupling.

* Memento: checkpointing, allows for undo via rollback.

* Null object/nullable type: avoid problems with null dereference.

* Observer: publish-subscribe, signals-slots, event-driven, observers are notified of any changes.

* Servant: provides behavior (methods) to a group of classes, objects for which the servant provides the service are taken as parameters.

* Specification: combining rules using boolean operators, mostly for data filtering.

* State: implement state machine where each state is a derived class calling parent interface methods.

* Strategy: enables selecting algorithm at runtime (e.g., validation algorithm based on incoming data).

* Template method: base class implements basic steps of an algorithm, specifics (variants) are implemented in derived classes.

* Visitor: separate algorithm from object structure on which it operates, allows for defining new operations without changing elements on which it operates. Visitor takes concrete elements as arguments.


### Architectural patterns

* Broker: coordination among components, for instance in between the client and servers.
* Client-server
* Layered: levels of abstraction, for instance UI layer, service, domain (business logic), persistence layer, e.g., general desktop app.
* Master-slave
* P2P
* Pipe-filter: `src | pipe1 | filter1 | pipe2 | filter2 | sink`, e.g., compiler.

#### MVC

* Model: data + state.
* View: lean, rendering UI, loosely coupled, not knowing what to do when the user presses the button (only forwards data).
* Controller: receives the input from the view and interacts with the model (e.g., activity in Android).

Problem is with the controller which is tightly coupled with a view and may get bloated, since most of the logic is there.

#### MVP

* Model: the same as in MVC.
* View: it is now up to the view which is a bit smarter than in MVC to determine which functions from the presenter to call.
* Presenter: is like a controller but is just an interface, not tied to the view in order to allow more flexibility.

#### MVVM

* Model: the same as in MVC.
* View: binds to the observables that are exposed by the viewmodel.
* Viewmodel: has observables for the view and allows the view to pass events to the model.


### Language-related concepts

* Declarative (functional, logic, reactive) vs imperative languages (procedural, object-oriented).
* Binding: early = at compile time (e.g., overloading), late (dynamic) = at run time (e.g., overriding).
* Introspection: ability to examine type or properties at runtime.
* Monkey patching: dynamic replacement of attributes at runtime.
* Reflection: modification of program structure at runtime.
* Single dispatch (depends on object type as in C++) vs double dispatch (depends both on object type and parameters).
* Static dispatch (e.g., function overloading) vs dynamic dispatch (for dynamic dispatch, declare a C++ method as virtual).

#### Object-oriented terminology

* Abstraction
* Encapsulation = hiding data
* Friend = defined outside a class but can access internal stuff
* Inheritance
* Interface = collection of methods (mostly abstract)
* [Overloading vs overriding](https://stackoverflow.com/questions/837864/java-overloading-vs-overriding): overloading refers to multiple methods with the same name but different parameters (return value doesn't matter, overloading is resolved at compile time), overriding refers to the redefinition of a function from the base class in the derived class (overriding is resolved at run-time).
* [Polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)) = more than one form, examples: function overloading (ad-hoc polymorphism), generics, inheritance.
* Virtual function = can be overridden


### Principles

* [ACID](https://en.wikipedia.org/wiki/ACID): for transactions: atomicity (all or nothing), consistency (one valid state to another), isolation (concurrent execution same result as sequential), durability (once committed remains so).

* [Broken windows theory](https://en.wikipedia.org/wiki/Broken_windows_theory): bad code encourages more bad code.

* [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem): only 2/3 guarantees are simultaneously possible: consistency (every read receives the most recent write or error), availability (every request has a response), partition tolerance (system works even if messages are dropped).

* [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete): create, read, update, delete, 4 basic functions of persistent storage.

* [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself): avoid redundancy.

* [KISS](https://en.wikipedia.org/wiki/KISS_principle): keep it simple, stupid.

* [Lint](https://en.wikipedia.org/wiki/Lint_(software)): tools which analyze source code in order to find bugs, errors, and suspicious constructs. There exits many linters for various languages and platforms.

* [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method): project planning: must have, should have, could have, won't have.

* [Not invented here](https://en.wikipedia.org/wiki/Not_invented_here): avoiding using products, guidelines, etc. created outside the company.

* [Occam's razor](https://en.wikipedia.org/wiki/Occam%27s_razor): one should select the answer that makes the fewest assumptions (simpler theories are preferable).

* [Principle of least astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment): components of the system should behave in an expected way, might apply to both the UI and the source code.

* [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization): constructor/destructor.

* [Reinventing the wheel](https://en.wikipedia.org/wiki/Reinventing_the_wheel): duplicating a common, known method.

* [SOLID](https://en.wikipedia.org/wiki/SOLID): single responsibility (per class), open/closed (open for extension, closed for modification, e.g., inheritance), Liskov substitution (subclass can be used as if it were its parent), interface segregation (expose only the required methods to clients), dependency inversion (program to an interface, not to an implementation).

* [SSOT](https://en.wikipedia.org/wiki/Single_source_of_truth): each data element is stored exactly once

* [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better): less functionality is sometimes preferable (e.g., easier to use).

* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it): don't add functionality until necessary.


### Project planning

* [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration): merging all working copies several times a day in order to mitigate integration problems.

* [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery): short cycles, software can be released at short notice.

* [Neutral build](https://en.wikipedia.org/wiki/Neutral_build): done in a neutral environment (outside deployment), catches errors such as different environmental variables, unchecked files, etc.

* [Nightly build](https://en.wikipedia.org/wiki/Daily_build): auto neutral build, mostly done when no one is working.

#### Things to consider

1. Specification, possibly start with abstract description and work towards the details.
1. Select the technologies and the development process.
1. Define features, perhaps in connection with the technologies.
1. Define the timeline: task planning, delegation, select a team, divide responsibilities, agree how progress/success will be measured/defined.
1. Before the start: check if we have everything we need (resources, etc.)

#### Scrum

[Scrum](https://en.wikipedia.org/wiki/Scrum_(software_development)): 3-9 people, sprints ~2 weeks, daily 15-minute stand-ups. [Agile](https://en.wikipedia.org/wiki/Agile_software_development), iterative, incremental, flexible.

* Development team
* Product owner = stakeholders
* Scrum master = servant-leader, helps the team


### Testing

A unit in a [unit test](https://en.wikipedia.org/wiki/Unit_testing) could be an entire module or interface or an individual method.
Unit tests are often combined with [matchers](https://en.wikipedia.org/wiki/Hamcrest) (Hamcrest) which extend simple assertions and allow for the use of a declarative style.

Common terms include:

* [A/B testing](https://en.wikipedia.org/wiki/A/B_testing): a controlled experiment (i.e. ideally varying only in what is tested) of two variants, e.g., testing two website designs for user engagement.

* [Behavior-driven development](https://en.wikipedia.org/wiki/Behavior-driven_development) (BDD): extension of TDD where tests are based on scenarios and descriptions.

* [Black-box testing](https://en.wikipedia.org/wiki/Black-box_testing): testing without knowing the internals.

* [Code coverage](https://en.wikipedia.org/wiki/Code_coverage): describe how much of source code is executed by unit tests. Could be measured in terms of functions, statements, branches, etc.

* [Fuzz test](https://en.wikipedia.org/wiki/Fuzzing): testing with invalid, unexpected, or random data. Related is [monkey testing](https://en.wikipedia.org/wiki/Monkey_testing) where random input is supplied to the program.

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

* `chmod [XXX] [file]` – change permissions to `[XXX]` (owner, group, anybody) for `[file]`, 4 = read, 2 = write, 1 = execute (can be combined)

* `df -h` – disk usage in human-readable

* `find / -name "*.txt" 2> /dev/null` – find all files with .txt extension while ignoring error messages

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

1. Preprocessing: handling preprocessor directives, i.e. parsing defines, includes, etc.
1. Compilation: produces object files (.o). These can be grouped into a static library (.a). Object files can refer to symbols that are declared but not defined.
1. Linking: combines object files into a dynamic library or an executable.


### Basic

* `assert(1 == 1 == 1)` doesn't fail, `assert(4 == 4 == 1)` doesn't fail, `assert(4 == 4 == 4)` fails, assert `assert(1 == 4 == 4)` fails.

* Abstract class has pure virtual functions: `virtual void fun() = 0;`. Each pure virtual function must be overridden for the class to be instantiated.

* Class has private fields/funs by default, struct has public fields/funs by default.

* Constructors: default (created when no other constructor is specified), parametric, copy, move.

* Placement new: `char *buf = new char[sizeof(string)];`, `string *p = new (buf) string("hi")`

* References cannot be null, reset or uninitialized.

* [Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)): destructor, copy constructor, copy assignment operator.

#### Bitwise operators

*TODO*

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

#### Memory management

`malloc`/`calloc` return NULL on error and they must be matched with `free`/`realloc`.
`new` must be matched with `delete` or `delete[]`, it throws `bad_alloc` on error or use `(std::nothrow)` to return NULL instead.

#### Operator overloading

```cpp
struct Num
{
    // Initializer list is useful when members are complex types,
    // as it avoids calling the default constructor.
    // Note: variables are initialized in the order of their declaration in the class.
    Num(int argN) : n(argN) { }

    friend Num operator+ (const Num &t1, const Num &t2)
    {
       return Num(t1.n + t2.n);
    }
    
    // Overloading the operator using a friend function allows for other types as arguments.
    friend Num operator+ (int n, const Num &t2)
    {
       return Num(n + t2.n);
    }

    Num& operator+= (const Num& other)
    {
        n += other.n;
        return *this;
    }

    int n;
};

int main() 
{
    Num num1 = Num(2) + Num(6);
    Num num2 = 2 + Num(6);

    cout << num1.n << " " << num2.n << endl;
    
    // This invokes the constructor of Num with 4 as argument.
    // It wouldn't work if the constructor were explicit.
    num2 += 4;

    cout << num1.n << " " << num2.n << endl;
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
    box.dumpVal<5>();
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

* [Template specialization](https://www.geeksforgeeks.org/template-specialization-c/) refers to specific template definitions for particular data types.
Explicit (full) specialization means that all template arguments are provided.

* [Partial specialization](https://en.wikipedia.org/wiki/Partial_template_specialization) means that only some arguments are provided.
In C++ partial specialization is not allowed for functions (either member or non-member functions), using overloading is suggested instead.

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

*TODO*

#### String

#### Vector


### C++11

* Use `-std=c++11` switch for compilation.

* Aggregate initialization (brace init): `vector<int> vec { 1, 2, 3 };`, `vector<vector<int>> vec { {1}, {2, 2}, {3} };`, `tuple<int, int, string> t1 { 2, 1, "ala" };`.

* `auto n = 5; cout << typeid(n).name() << endl;` prints `i`.

* `constexpr`: a constant value which must be initialized at compile time.

* `for (const int i : tab) { }` works for arrays and containers with `begin()` and `end()`.

* Enum class values require scoping: `enum class Letters { A, B, C }; cout << (int)Letters::A << endl;`

* Initializer list is iterable: `for (int i : { 1, 2, 3}) { cout << i << endl; }`.

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

#### Lambdas

```cpp
sort(tab, tab + n, [](int a, int b) { return a > b; });
```

Assigning a lambda to a variable:

```cpp
auto fun = []() { cout << "lambda" << endl; };
fun(); // prints lambda
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

```cpp
MyString(const MyString &other) { }
MyString(MyString &&other) { } // steal the resources from other

MyString &operator= (MyString other) // pass-by-value
{
  swap(other);
  return *this;
}
```

#### Multithreading

Before C++11 it was required to use OS-specific functionality, e.g., pthreads on Linux.
Compile with `-pthread` on Linux.

* Launching a simple thread:

```cpp
thread t1([]() { cout << "t1" << endl; });
t1.join(); // Blocks until t1 finishes
```

* Atomic access:

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

* Call once:

```cpp
vector<thread> threads;

once_flag flag1;
auto once = [&flag1]() { call_once(flag1, []() { cout << "Called!" << endl; }); };

for (int i = 0; i < 5; ++i)
{
    threads.push_back(thread(once));
} // Will print "Called!" only once.
```

* Threads with synchronization:

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

* Thread with a timed mutex (i.e. with a timeout):

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

* Threads with blocking on the result:

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

* Threads with a condition variable:

```cpp

```

* `future<void> res(async(fun));`: async can take fun with args or a lambda, `res.get();` blocks until the result is available.
* `std::promise` is the producer and `std::future` is the consumer.

#### Smart pointers

* `shared_ptr<int>tab (new int[size]);`: resource is deallocated when the last pointer is destroyed. Thread-safe for reference counting, not thread-safe for pointed object access.

Shared pointer can be created using the `make_shared` function:

```cpp
struct Test { int a; };
auto ptr = make_shared<Test>(); // ptr is a shared_ptr<Test>
cout << ptr->a << endl;
```

* `weak_ptr`: doesn't increase the count, useful for preventing circular dependencies.
* `unique_ptr`: only one reference, cannot be copied, move semantics allow for ownership transfer.

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

### C++14

* Use `-std=c++14` switch for compilation.
* Binary literals: `cout << 0b10001 << endl` prints 17.

### C++17 

* Use `-std=c++17` switch for compilation.

*TODO*

### Makefile

```makefile
# First macros are provided. These can be uncommented with '#' if needed.
CC        = g++                          # Compiler name
EXE       = sopang                       # Executable name
CCFLAGS   = -Wall -pedantic -std=c++11   # Compiler flags: all warnings, pedantic, C++11 standard.
OPTFLAGS  = -DNDEBUG -O3                 # Option flags: define NDEBUG (disables assert()), opti level 3.

INCLUDE   = -I/path/to/lib               # -I: add directory searched for header files.
LDFLAGS   = -L/path/to/lib               # -L: add directory searched for -l.

# Link with the library libm.a (static) or libm.so (shared, dynamic).
# Use -static to prefer static to dynamic linking (i.e. search for .a files first).
LDLIBS    = -lm

# Default rule is all.
all: $(EXE)

# Executable depends on the following object files. $@ is the target name, $^ are the dependencies.
$(EXE): main.o sopang.o
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(INCLUDE) $(LDFLAGS) $^ -o $@ $(LDLIBS)

# Object file main.o depends on the following files.
# -c means stop after compilation (no linking), this produces the object file.
main.o: main.cpp helpers.hpp params.hpp
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(INCLUDE) -c main.cpp

sopang.o: sopang.cpp sopang.hpp helpers.hpp
	$(CC) $(CCFLAGS) $(OPTFLAGS) $(INCLUDE) -c sopang.cpp

.PHONY: clean # Phony targets are not associated with file dependencies.

clean:
	rm -f main.o sopang.o $(EXE)

rebuild: clean all
```

Python
--------------------

[Python](https://en.wikipedia.org/wiki/Python_(programming_language)): interpreted, object-oriented, garbage-collected, name binding, duck typing (based on runtime object interface),  many libraries. Reference interpreter is called CPython, other: PyPy which is based on JIT. Stuff below is relevant to Python2.

[Not great](https://stackoverflow.com/questions/1017621/why-isnt-python-very-good-for-functional-programming) for functional programming:

* no tail recursion (i.e. no using equivalent memory to a loop)
* no pattern matching
* not too many list functions
* no concise way to combine functions

### Selected features

* `[1,2,3] == [1,2] + [3]`

* `[1,2,3,4][1 : 3] == [2,3]`, `[1,2,3][ : 1] == [1]`

* `[1,2,3,4][::2] == [1,3]`, `[1,2,3][::-1] == list(reversed([1,2,3]))`

* `l = [[]] * 5`: same reference replicated, doesn't work as expected. Use `l = [[] for _ in xrange(5)]` instead.

* Deep copy: `l = copy.deepcopy(x)`, works with nested lists.

* `dir(obj)` returns a list of defined members (functions and variables).

* Functions are first-class citizens in Python, nested functions are allowed, functions can be assigned, returned, etc.

* Import from subdir requires a present `__init__.py` file (may be empty).

* `reverse(l)` returns an iterator to `l` (if `l` changes, data pointed to by an iterator changes too).

* Serialization (translating data to storage/transmission format) can be realized using `pickle` or `cPickle` (the latter is faster).

* Tertiary operator: `x = 2 if len(s) > 5 else 10`

* Tuple `(1,2,3)` is immutable.

* `with` works like try/finally, requires context management protocol: `__enter__()`, `__exit()__`.

* `xrange` and `range` start from 0, Python2: `xrange` is a generator and `range` creates a list, in Python3 there is only `range` which is a generator.

* `zip([1,2,3],[4,5,6]) == [(1,4), (2,5), (3,6)]`

### List functions

* `del l[1]` removes an element at index 1.
* `l.pop(1)` removes an element at index 1 and returns this element.
* `l.pop(l.index(max(l)))` removes the max element.
* `l.remove(x)` removes the first value matching `x`.

### Functions

#### Calling with args

```python
def add(x, y):
  return x + y

def add3(x, y = 3):
  return x + y

def addStar(*args): # All params as a tuple
  return sum(args)
```

* Default arg values must follow from the left.
* Calling with explicit arg names: `print add(x = 5, y = 4)`.
* `print addStar(1, 2, 3)`
* Unpacking operator: `print add(*[1, 2])`
* Partial application (argument binding): `add5 = functools.partial(lambda x,y: x + y, 5)`

#### Keyword args

```python
def addKwargs(**kwargs): # All keyword params as a dict
  return sum(kwargs.values())
```

* `print addKwargs(x = 2, y = 3)`
* `print addKwargs(**{"x": 2, "y" = 3})`

### Filter, map, reduce

* List comprehension combines map with filter: `[2 * x for x in xrange(10) if x % 2 == 0]`.
* `map(lambda x: 2 * x, filter(lambda x: x % 2 == 0, xrange(10)))`
* `map(len, ["ala","ma","kota"]) == [3,2,4]`
* `sum([1,2,3]) == reduce(lambda x,y: x + y, [1,2,3], 0)`

### Classes

```python
class Point(object):
  n = 5 # Static var, access as Point.n

  def __init__(self, x, y):
    self.x = x
    self.y = y

  def mysum(self): # Not passing self would mean a static function
    return self.x + self.y
```

* Always inherit from `object` for access to class names (new-style classes).
* Convention for private: `self._x`, private with a mangled name: `self.__x` (works for both functions and variables).
* Dictionary containing all member variables: `print p1.__dict__`
* Extend objects: `p1.z = 8`, now `print p1.z` works (only if z was set for this object).

#### Inheritance

```python
class Point3D(Point):
  def __init__(sefl, x, y, z):
    Point.__init__(self, x, y)
    self.z = z

  def mysum(self):
    return Point.mysum(self) + self.z
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

plt.plot([1,2,3], [4,5,6], "ko-")
plt.show()
```

Git
--------------------

#### [Basic commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)

* `git init`
* `git clone [address]`
</br>

* `git add -u` – add all already-tracked files
* `git add .` – add all files from the current directory, also untracked
* `git checkout [branch-name]` – switch to branch `[branch-name]`
* `git checkout -b [branch-name] [base-branch-name]` – create a branch `[branch-name]` out of `[base-branch-name]`
* `git commit -a` – commits changes to all tracked files (not only in the current directory)
* `git commit -m "[msg]"` – commit with message `[msg]`
* `git diff [file]` – show unstaged changes for `file`, `git diff --staged` to show all staged changes, `git diff --staged [file]` to show all staged changes for `file`
* `git merge [branch-name]` – merge current branch with branch `[branch-name]`
* `git push` – push local to to the corresponding remote branch
* `git push origin [branch-name]` – push only branch `[branch-name]`
* `git rebase [branch-name]` – moves the entire current branch to the tip of `[branch-name]`
</br>

* `git log` – show all commits starting from the latest one, `git log -p` to show changes alongside
* `git pull` (this is `git fetch` followed by `git merge` to the current local branch)
* `git reset --hard origin/master` – remove all local changes
* `git rm [file]` – remove `[file]`
* `git rm --cached [file]` – stop `[file]` from being tracked

#### Related terminology

* [Pull request](https://yangsu.github.io/pull-request-tutorial/): request that a maintainer (somebody in the authority) pull the changes and merge them after approval (i.e. add them into the codebase).

#### GitFlow

[GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) is a workflow model based on branches.

* **master** branch: releases with version numbers (main branch number 1)
* **develop** branch: integration branch for features (main branch number 2)
<br />

* **feature**: branched out of and into develop, single feature = single branch
* **hotfix**: quick patches, the only branch out of master, merged both with master and develop/release
* **release**: branched out of develop, no new features can be added, merged into master when ready to ship, next also merged back into develop

This is in opposition to a [centralized](https://www.atlassian.com/git/tutorials/comparing-workflows) (SVN-like) workflow, where all features are branched out of and merged into a single master branch.
