General
--------------------

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
* [Heap](https://en.wikipedia.org/wiki/Heap_(data_structure)) – priority queue, max-heap or min-heap.

##### String matching

* [Suffix array](https://en.wikipedia.org/wiki/Suffix_array)

* [Suffix tree](https://en.wikipedia.org/wiki/Suffix_tree)

* [Trie](https://en.wikipedia.org/wiki/Trie)

### Algorithms

##### Graphs

* [A*](https://en.wikipedia.org/wiki/A*_search_algorithm)

* [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) – specific case of A* without a heuristic.

##### Trees

* [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm) – minimum spanning tree. Divide all nodes into a forest, always take the shortest edge, span only if spanning two distinct trees, otherwise discard.

##### String matching


### Design patterns

##### Creational

The following summary is based on [Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern) page.

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

### Programming languages

Declarative (functional, logic, reactive) vs imperative languages (procedural, object-oriented).

### Unit testing

### Useful Linux commands

##### General

* `cat [file]` – print file contents
* `chmod [XXX] [file]` – change permissions to `[XXX]` (owner, group, anybody) for `[file]`, 4 = read, 2 = write, 1 = execute
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

[Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))

##### Memory management

`malloc` must be matched with `free`, it returns NULL on error.
`new` must be matched with `delete` or `delete[]`, it throws `bad_alloc` on error or use `(std::nothrow)` to return NULL instead.

##### Variadic functions

`int printf(const char* format, ...)`. Init with `va_list` , then `va_start`, `va_arg` for accessing each arg, finish with `va_end`.

##### Operator overloading

### C++11

[Rule of five](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)#Rule_of_Five)

##### Lambdas

##### Multithreading

##### Smart pointers

### C++14/17


Python
--------------------

Python: interpreted, object-oriented, garbage-collected, name binding, duck typing (based on runtime object interface),  many libraries. Reference interpreter is called CPython, other: PyPy which is based on JIT.

[Not great](https://stackoverflow.com/questions/1017621/why-isnt-python-very-good-for-functional-programming) for functional programming:

* no tail recursion (i.e. no using equivalent memory to a loop)
* no pattern matching
* not too many list functions
* no concise way to combine functions

### Main features

* Import from subdir requires a present `__init__.py` file (may be empty).

* `xrange` and `range` start from 0, Python2: `xrange` is a generator and `range` creates a list, in Python3 only `range` which is a generator.

* `zip([1,2,3],[4,5,6]) == [(1,4), (2,5), (3,6)]`

### Function calling

##### Calling with args

```
def add(x, y):
  return x + y

def add3(x, y = 3):
  return x + y
```

* Default arg values must follow from the left.
* Calling with explicit arg names: `print add(x = 5, y = 4)`.
* Unpacking operator: `print add(*[2, 3])`
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
