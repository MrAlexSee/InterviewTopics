General
--------------------

### Basic math

* Arithmetic series sum: n(n + 1) / 2 = ϴ(n²)
* Harmonic series sum: 1 + 1/2 + 1/3 + ... + 1/n = ln n + O(1)

##### Graphs

* Bipartite:
* Complete graph: every pair of verticies is adjacent, no loops
* Strongly connected: every 2 vertices are reachable from each other

### Complexity

* o, O, ϴ, Ω, ω
* P, NP, NP-hard, NP-complete, P vs NP

### Data structures

##### Basic

Average cases are presented. BST is assumed to be balanced, hashing a simple item is assumed to be constant-time.
For the hash table worst-case for all operations is O(n).

Structure  | Access   | Search   | Insert/delete  | Space
---------- | -------- | ---------| -------------- | -------
Array      | O(1)     | O(n)     | O(n)           | O(n)
List       | O(n)     | O(n)     | O(1)           | O(n)
BST        | O(log n) | O(log n) | O(log n)       | O(n)
Hash table | O(1)     | O(1)     | O(1)           | O(n)

* BST balanced flavors: [AVL](https://en.wikipedia.org/wiki/AVL_tree), [red-black](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree), [Treap](https://en.wikipedia.org/wiki/Treap)

* [Heap](https://en.wikipedia.org/wiki/Heap_(data_structure)): priority queue, max-heap or min-heap.

##### String matching

* [Suffix array](https://en.wikipedia.org/wiki/Suffix_array)

* [Suffix tree](https://en.wikipedia.org/wiki/Suffix_tree)

* [Trie](https://en.wikipedia.org/wiki/Trie)

### Algorithms

##### Graphs

* [A*](https://en.wikipedia.org/wiki/A*_search_algorithm)

* [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm): specific case of A* without a heuristic.

##### Trees

* [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm): minimum spanning tree. Divide all nodes into a forest, always take the shortest edge, span only if spanning two distinct trees, otherwise discard.

##### String matching

*TODO*

### Design patterns

##### Creational

The following summary is based on [Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern) page. Obvious patterns are only listed and not described.

* Abstract factory: encapsulate individual factories under a generic interface

* Builder: separate construction from interpretation

* Dependency injection

* Factory

* Lazy initialization

* Multiton: registry of singletons

* Object pool

* Prototype: create new objects from a skeleton

* RAII: constructor/destructor

* Singleton

##### Structural

* Adapter: wrapper

* Bridge: decouple abstraction from implementation in order to facilitate changes

* Composite: groups of objects treated the same as a single object

* Decorator: dynamically add behavior to an individual object, without affecting the behavior of other objects (i.e. alter behavior at runtime)

* Extension

* Facade: a higher-level interface which is easier to use

* Flyweight: use sharing to support large numbers of similar objects efficiently

* Marker: use an empty interface to indicate specific behavior (e.g., Serializable)

* Proxy: used in order to control access to an object

* Twin: multiple inheritance in languages that do not support it (two closely coupled subclasses, each derived from one superclass)

##### Behavioral

* Blackboard: knowledge sources publish potential solutions on the blackboard, control component is in between

* Chain of responsibility: a chain of processing objects receives the commands which are handled or passed along. Essentially if..elif..else which can be dynamically reconfigured.

* Command: object encapsulates all information needed to perform an action at a later time, including the receiver

* Interpreter: use of DSLL, e.g., SQL, user interface descriptions

* Iterator: decouples algorithms from containers

* Mediator: encapsulates communication between objects, reduces coupling

* Memento: checkpointing, allows for undo via rollback

* Null object/nullable type: avoid problems with null dereference

* Observer: publish-subscribe, signals-slots, event-driven, observers are notified of any changes

* Servant: provides behavior (methods) to a group of classes, objects for which the servant provides the service are taken as parameters

* Specification: combining rules using boolean operators, mostly for data filtering

* State: implement state machine where each state is a derived class calling parent interface methods

* Strategy: enables selecting algorithm at runtime (e.g., validation algorithm based on incoming data)

* Template method: base class implements basic steps of an algorithm, specifics (variants) are implemented in derived classes

* Visitor: separate algorithm from object structure on which it operates, allows for defining new operations without changing elements on which it operates. Visitor takes concrete elements as arguments.

### Architectural patterns

* Broker: coordination among components, for instance in between the client and servers
* Client-server
* Layered: levels of abstraction, for instance UI layer, service, domain (business logic), persistence layer, e.g., general desktop app
* Master-slave
* P2P
* Pipe-filter: `src | pipe1 | filter1 | pipe2 | filter2 | sink`, e.g., compiler

#####
MVC

* model: data + state
* view: lean, rendering UI, loosely coupled, not knowing what to do when the user presses the button (only forwards data)
* controller: receives the input from the view and interacts with the model

Problem is with the controller which is tightly coupled with a view and may get bloated, since most of the logic is there.

#####
MVP

* model: the same as in MVC
* view: it is now up to the view which is a bit smarter than in MVC to determine which functions from the presenter to call
* presenter: is like a controller but is just an interface, not tied to the view in order to allow more flexibility

#####
MVVM

* model: the same as in MVC
* view: binds to the observeables that are exposed by the viewmodel
* viewmodel: has observables for the view and allows the view to pass events to the model

### Principles

* [ACID](https://en.wikipedia.org/wiki/ACID): for transactions: atomicity (all or nothing), consistency (one valid state to another), isolation (concurrent execution same result as sequential), durability (once committed remains so)

* [Broken windows](https://en.wikipedia.org/wiki/Broken_windows_theory): bad code encourages more bad code.

* [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem): only 2/3 guarantees are simultanously possible: consistency (every read receives the most recent write or error), availability (every request has a response), partition tolerance (system works even if messages are dropped)

* [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete): create, read, update, delete, 4 basic functions of persistent storage.

* [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself): avoid redundancy.

* [KISS](https://en.wikipedia.org/wiki/KISS_principle): keep it simple, stupid.

* [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method): project planning: must have, should have, could have, won't have.

* [Not invented here](https://en.wikipedia.org/wiki/Not_invented_here): avoiding using products, guidelines etc. created outside the company.

* [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization): constructor/destructor.

* [Reinventing the wheel](https://en.wikipedia.org/wiki/Reinventing_the_wheel): duplicating a common method.

* [SOLID](https://en.wikipedia.org/wiki/SOLID): single responsibility (per class), open/closed (open for extension, closed for modification, e.g., inheritance), Liskov substitution (subclass can be used as parent), interface segregation (expose only the required methods to clients), dependency inversion (program to interface, not an implementation).

* [SSOT](https://en.wikipedia.org/wiki/Single_source_of_truth): each data element is stored exactly once

* [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better): less functionality is sometimes preferable (e.g., easier to use).

* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it): don't add functionality until necessary.

### Project planning

* [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration): merging all working copies several times a day in order to mitigate integration problems.

* [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery): short cycles, software can be released at short notice.

* [Neutral build](https://en.wikipedia.org/wiki/Neutral_build): done in a neutral environment (outside deployment), catches errors such as different environmental variables, unchecked files, etc.

* [Nightly build](https://en.wikipedia.org/wiki/Daily_build): auto neutral build, mostly done when no one is working.

##### Things to consider

1. Specification, possibly start with abstract description and work towards the details.
1. Select the technologies and the development processing.
1. Define features, perhaps in connection with the technologies.
1. Define the timeline: task planning, delegation, select a team, divide responsibilities, agree how progress/success will be measured/defined.
1. Before the start: check if we have everything we need (resources, etc.)

##### Scrum

[Scrum](https://en.wikipedia.org/wiki/Scrum_(software_development)): 3-9 people, sprints ~2 weeks, daily 15-minute stand-ups. Iterative, incremental, flexible.

* Product owner = stakeholders
* Development team
* Scrum master = servant-leader, helps the team

### Language-related concepts

* Declarative (functional, logic, reactive) vs imperative languages (procedural, object-oriented).
* Binding: early = at compile time (e.g., overloading), late (dynamic) = at run time (e.g., overriding).
* Introspection: ability to examine type or properties at runtime
* Monkey patching: dynamic replacement of attributes at runtime
* Reflection: modification of program structure at runtime
* Static dispatch (e.g., function overloading) vs dynamic dispatch (for dynamic dispatch, declare a C++ method as virtual)
* Single dispatch (depends on object type as in C++) vs double dispatch (depends both on object type and parameters)

##### Object-oriented terminology

* Abstraction
* Encapsulation = hiding data
* Friend = defined outside a class but can access internal stuff
* Inheritance
* Interface = collection of methods (mostly abstract)
* Polymorphism = using subclasses (more than one form)
* Virtual function = can be overridden

### Unit testing

*TODO*

* [Hamcrest](https://en.wikipedia.org/wiki/Hamcrest) (matchers)

### Useful Linux commands

##### General

* `cat [file]` – print file contents
* `chmod [XXX] [file]` – change permissions to `[XXX]` (owner, group, anybody) for `[file]`, 4 = read, 2 = write, 1 = execute (can be combined)
* `df -h` – disk usage in human-readable
* `ls -lah` – list current dir with hidden files and details in human-readable
* `man gcc | grep [-]std=c++11 -C2` – search for a switch and show 2 lines around the result
* `mv [src] [dst]` – move file `[src]` to `[dst]`, can be used for renaming
* `rm -rf [dir]` – remove `[dir]` recursively
* `touch [file]` – create `[file]`
* `whreis [cmd]` – check the location of `[cmd]`

##### Packages

* `apt-get update` – update package index
* `apt-get dist-upgrade` – install update and satisfy dependencies
* `dpkg --listfiles [pkg]` – list all files from package `[pkg]`
* `update-alternatives --config [pkg]` – select a different version for `[pkg]`

##### Conversions

* `dot -Tpdf [in].dot -o [out].pdf` – convert file `[in]` to `[out].pdf`
* `rsvg-convert -f pdf -o [out].pdf [in]` – convert file `[in]` to `[out].pdf`

##### Net

* `host [url]` – get IP for `[url]`
* `wget -m -e robots=off --no-parent [url]` – download recursively from `[url]`
* `whois [IP]` – get information about `[IP]`

##### Compression

* `tar -xzf [in]` – extract, gunzip (j = bzip), input file `[in]`
* `unzip [file]`
* `zip [out] [file1] [file2]`

C++
--------------------

### Basic

* Abstract class has pure virtual functions: `virtual void fun() = 0;`

* Class has private fields by default, struct public by default.

* Constructors: default (created when no other constructor is specified), parametric, copy, move

* Placement new: `char *buf = new char[sizeof(string)];`, `string *p = new (buf) string("hi")`

* References cannot be null, reset or uninitialized.

* [Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) – destructor, copy constructor, copy assignment operator.

##### Memory management

`malloc` must be matched with `free`, it returns NULL on error.
`new` must be matched with `delete` or `delete[]`, it throws `bad_alloc` on error or use `(std::nothrow)` to return NULL instead.

##### Operator overloading

```
Type operator+ (const Type &type);
friend Type operator+ (const Type &t1, const Type &t2);
```

##### Variadic functions

`int printf(const char* format, ...)`. Init with `va_list` , then `va_start`, `va_arg` for accessing each arg, finish with `va_end`.

### C++11

* `for (const int i : tab) { }`

* Mark overriden (virtual) functions with `override` keyword.

* [Rule of five](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)#Rule_of_Five): destructor, copy constructor, move constructor, copy assignment operator, move assignment operator

##### Move semantics

* lvalue = has address can be assigned
* rvalue = a temporary object `string getName() { return "ala"; } string &&name = getName();`

```
MyString(const MyString &other) { }
MyString(MyString &&other) { } // steal the resources

MyString &operator= (MyString other) // pass-by-value
{
  swap(other);
  return *this;
}
```

##### Lambdas

```
sort(tab, tab + n, [](int a, int b) { return a > b; });
```
Lambdas automatically capture constants, in addition: `[x]` captures `x` by value, `[&x]` captures x by reference.

`transform(tab, tab + n, tab, [&z](int x) { return x + z; });` works like map

##### Multithreading

* `std::promise` is the producer and `std::future` is the consumer.
* `future<void> res(async(fun));` – async can take fun with args or a lambda, `res.get();` blocks until the result is available.


##### Smart pointers

* `shared_ptr<int>tab (new int[size]);` – resource is deallocated when the last pointer is destroyed.
* `weak_ptr` – doesn't increase the count, useful for preventing circular dependencies.
* `unique_ptr` – only one reference, cannot be copied.

### C++14/17

*TODO*

Python
--------------------

Python: interpreted, object-oriented, garbage-collected, name binding, duck typing (based on runtime object interface),  many libraries. Reference interpreter is called CPython, other: PyPy which is based on JIT. Stuff below is relevant to Python2.

[Not great](https://stackoverflow.com/questions/1017621/why-isnt-python-very-good-for-functional-programming) for functional programming:

* no tail recursion (i.e. no using equivalent memory to a loop)
* no pattern matching
* not too many list functions
* no concise way to combine functions

### Selected features

* `l = [[]] * 5`: same reference replicated, doesn't work as expected. Use `l = [[] for _ in xrange(5)]` instead.

* Deep copy: `l = copy.deepcopy(x)`, works with nested lists

* `dir(obj)`: returns a list of defined members (functions and variables)

* Functions are first-class citizens in Python, nested functions are allowed, functions can be assigned, returned, etc.

* Import from subdir requires a present `__init__.py` file (may be empty).

* `reverse(l)` returns an iterator to `l` (if `l` changes, data pointed to by iterator changes too)

* Serialization (translating data to storage/transmission format) can be realized using `pickle` or `cPickle` (faster).

* Tertiary operator: `x = 2 if len(s) > 5 else 10`

* Tuple `(1,2,3)` is immutable.

* `with` works like try/finally, requires context management protocol: `__enter__()`, `__exit()__`.

* `xrange` and `range` start from 0, Python2: `xrange` is a generator and `range` creates a list, in Python3 only `range` which is a generator.

* `zip([1,2,3],[4,5,6]) == [(1,4), (2,5), (3,6)]`

### List functions

* `del l[1]` removes element at index 1.
* `l.pop(1)` removes element at index 1 and returns this element.
* `l.pop(l.index(max(l)))` removes the max element.
* `l.remove(x)` removes the first value matching `x`.

### Functions

##### Calling with args

```
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
* Unpacking operator: `print add(*[1, 2, 3])`
* Partial application (argument binding): `add5 = functools.partial(lambda x,y: x + y, 5)`


##### Keyword args

```
def addKwargs(**kwargs): # All keyword params as a dict
  return sum(kwargs.values())
```

* `print addKwargs(x = 2, y = 3)`
* `print addKwargs(**{"x": 2, "y" = 3)`

### Filter, map, reduce

* List comprehension combines map with filter, `[2 * x for x in xrange(10) if x % 2 == 0]`.
* `map(lambda x: 2 * x, filter(lambda x: x % 2 == 0, xrange(10)))`
* `map(len, ["ala", "ma", "kota"])`
* `sum([1,2,3]) == reduce(lambda x,y: x + y, [1,2,3], 0)`

### Classes

```
class Point(object):
  n = 5 # Static var, access as Point.n

  def __init__(self, x, y):
    self.x = x
    self.y = y

  def mysum(self): # Not passing self would mean a static function
    return self.x + self.y
```

* Always inherit from `object` for access to class names (new-style classes).
* Convention for private: `self._x`, private with mangled name: `self.__x` (works for both functions and variables).
* Dictionary containing all member variables: `print p1.__dict__`
* Extend objects: `p1.z = 8`, now `print p1.z` works only if z was set for this object.

##### Inheritance

```
class Point3D(Point):
  def __init__(sefl, x, y, z):
    Point.__init__(self, x, y)
    self.z = z

  def mysum(self):
    return Point.mysum(self) + self.z
```

Git
--------------------

[Basic commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html):

* `git init`
* `git clone [address]`
</br>

* `git add -a` – add all already-tracked files
* `git checkout [branch-name]` – switch to branch `[branch-name]`
* `git commit -m "[msg]"` – commit with message `[msg]`
* `git merge [branch-name]` – merge current branch with branch `[branch-name]`
* `git push` – push local to to the corresponding remote branch
* `git push origin [branch-name]` – push only branch `[branch-name]`
* `git rebase [branch-name]` – moves the entire current branch to the tip of `[branch-name]`
</br>

* `git log`
* `git pull` (this is `git fetch` followed by `git merge` to the current local branch)
* `git reset --hard origin/master` – remove all local changes
* `git rm [file]` – remove `[file]`
* `git rm --cached [file]` – stop `[file]` from being tracked

### GitFlow

[GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow): workflow model based on branches.

* **master** branch: releases with version numbers
* **develop** branch: integration branch for features

* **feature**: branched out of and into develop, single feature = single branch
* **release**: branched out of develop, no new features can be added, merged into master when ready to ship, next also merged back into develop
* **hotfix**: quick patches, the only branch out of master, merged both with master and develop/release

This is in opposition to a [centralized](https://www.atlassian.com/git/tutorials/comparing-workflows) (SVN-like) workflow, where all features are are branched out of and merged into a single master branch.
