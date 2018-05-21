General
--------------------

### Data structures

##### Basic

BST is assumed to be balanced.
Average case for the hash table (hashing a simple item is assumed to be constant-time), worst-case is `O(n)`.

Structure  | Access   | Search   | Insert/delete  | Space
---------- | -------- | ---------| -------------- | -------
Array      | O(1)     | O(n)     | O(n)           | O(n)
List       | O(n)     | O(n)     | O(1)           | O(n)
BST        | O(log n) | O(log n) | O(log n)       | O(n)
Hash table | O(1)     | O(1)     | O(1)           | O(n)


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

* [Broken windows](https://en.wikipedia.org/wiki/Broken_windows_theory): bad code encourages more bad code.

* [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself): avoid redundancy.

* [KISS](https://en.wikipedia.org/wiki/KISS_principle): keep it simple, stupid.

* [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method): project planning: must have, should have, could have, won't have.

* [Not invented here](https://en.wikipedia.org/wiki/Not_invented_here): avoiding using products, guidelines etc. created outside the company.

* [RAII](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization): constructor/destructor.

* [Reinventing the wheel](https://en.wikipedia.org/wiki/Reinventing_the_wheel): duplicating a common method.

* [SOLID](https://en.wikipedia.org/wiki/SOLID):

* [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better): less functionality is sometimes preferable (e.g., easier to use).

* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it): don't add functionality until necessary.

### Project planning

### Unit testing

### Useful Linux commands

* `cat [file]`: print file contents
* `chmod [XXX] [file]`: change permissions to `[XXX]` (owner, group, anybody) for `[file]`, 4 = read, 2 = write, 1 = execute
* `df -h`: disk usage in human-readable
* `ls -lah`: list current dir with hidden files and details in human-readable
* `man gcc | grep [-]std=c++11 -C2`: search for a switch and show 2 lines around the result
* `mv [src] [dst]`: move file `[src]` to `[dst]`, can be used for renaming
* `rm -rf [dir]`: remove `[dir]` recursively
* `touch [file]`: create `[file]`
* `whreis [cmd]`: check the location of `[cmd]`

* `dpkg --listfiles [pkg]`: list all files from package `[pkg]`
* `update-alternatives --config [pkg]`: select a different version for `[pkg]`

* `dot -Tpdf [in].dot -o [out].pdf`: convert file `[in]` to `[out].pdf`
* `rsvg-convert -f pdf -o [out].pdf [in]`: convert file `[in]` to `[out].pdf`

* `host [url]`: get IP for `[url]`
* `wget -m -e robots=off --no-parent [url]`: download recursively from `[url]`
* `whois [IP]`: get information about `[IP]`

* `tar -xzf [in]`: extract, gunzip (j = bzip), input file `[in]`
* `unzip [file]`
* `zip [out] [file1] [file2]`

C++
--------------------

### Basic

[Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)):

##### Memory management

`malloc` must be matched with `free`.
`new` must be matches with `delete` or `delete[]`.

##### [Variadic functions](http://en.cppreference.com/w/cpp/utility/variadic)

`int printf(const char* format, ...)`
Init with `va_list` , then `va_start`, `va_arg` for accessing each arg, finish with `va_end`.

##### Operator overloading

### C++11

[Rule of five](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)#Rule_of_Five):

##### Lambdas

##### Multithreading

##### Smart pointers

### C++14/17


Python
--------------------

### List comprehension

[Git](https://en.wikipedia.org/wiki/Git)
--------------------

[Basic commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html):

* `git init`
* `git clone [address]`

* `git add -a`: add all already-tracked files
* `git checkout [branch-name]`: switch to branch `[branch-name]`
* `git commit -m "[msg]"`: commit with message `[msg]`
* `git merge [branch-name]`: merge current branch with branch `[branch-name]`
* `git push`: push local to to the corresponding remote branch
* `git push origin [branch-name]`: push only branch `[branch-name]`
* `git rebase [branch-name]`: moves the entire current branch to the tip of `[branch-name]`

* `git log`
* `git pull` (this is `git fetch` followed by `git merge` to the current local branch)
* `git reset --hard origin/master`: remove all local changes
* `git rm [file]`: remove `[file]`
* `git rm --cached [file]`: stop `[file]` from being tracked


[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration): merging all working copies several times a day in order to mitigate integration problems.

[Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery): short cycles, software can be released at short notice.

### GitFlow

[GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow): workflow model based on branches.

* **master** branch: releases with version numbers
* **develop** branch: integration branch for features

* feature: branched out of and into develop, single feature = single branch
* release: branched out of develop, no new features can be added, merged into master when ready to ship, next also merged back into develop
* hotfix: quick patches, the only branch out of master, merged both with master and develop/release

This is in opposition to a [centralized](https://www.atlassian.com/git/tutorials/comparing-workflows) (SVN-like) workflow, where all features are are branched out of and merged into a single master branch.
