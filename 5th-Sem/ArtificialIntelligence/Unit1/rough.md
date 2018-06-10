# Problem Solving

## Some Definition

### 1. Problem Solving agent

* decides what to do by finding sequence of actions that leads to desirable output.

### 2. Problem Solving

* may be characterized by a systematic search through a range of possible actions.
* in order to reach some predefined goal or solution.

Categorized into two types:

1. Special Purpose:

    * Tailor made for a particular problem.
    * often exploits very specific features of the situation in which the problem is embedded.

2. General Purpose:

    * applicable to variety of problem.

Problem Solving Steps:

1. Goal Formulation.
2. Problem Formulation : Set of states, Goal test Function, Successor Function, Path Cost function.
3. Search.
4. Execute.

Importance of Searching in AI:

* Fundamental to Problem solving process
* When direct solution is not known.
* provides a framework.

### 3. Problem

A problem can be defined formally by four components:

1. Initial State: Start state
2. Successor Function: description of possible actions available to agent.
3. Goal test
4. Path Cost

### 4. State Space

* Set of all states reachable from initial state.
* The state space forms a graph (or map) in which the nodes represent states and the arcs between the nodes are actions.
* A path in state space is a sequence of states connected by sequence of actions.

### 5. Solution

* A solution in state space is the path from initial sate to goal states.

Components:

* Path/Solution Cost: A function that assigns a numeric cost to each path.
* Solution  Quality: Measured by the path cost function. Optimal Solution has the least path cost.

### 6. Search Problem

A search problem consists of the following:

* S -> full set of states.
* S0 -> Initial State
* A -> Set of actions
* G -> Set of final states

The search problem is to find a sequence of actions to lead the agent from initial state to a goal state. Sequence of action is called solution plan.

### 7. Production System

* Also called Expert System, Rule Based System, Condition Action System, Knowledge Based System, Production Rule System.
* is a computer Program typically used to provide some form of Artificial Intelligence.
* It primarily consists of a set of rules about behavior called `Production`.
* A Production System provides the mechanisms necessary to execute productions in order to achieve some goal for the system.
* It consists of two parts :
    1. A Sensory Precondition ( or IF Statement)
    2. An action ( THEN statement )
* if the production's precondition matches the current state of the world, then the production is said to be `triggered`.
* if the production action is executed then it is said to be `fired`.
* the underlying idea of production system is to represent knowledge in the form of condition-action pairs called production rules.

        IF CONDITION C is satisfied THEN the ACTION A is appropriate

* Architecture:
    1. Short Term Memory
    2. Set of Production Rules
    3. Interpreter

Example: Sorting String

    Production Set:
    1. ba -> ab
    3. ca -> ac
    4. cb -> bc

    Interpreter: Choose one of the rules according to some strategy.
    Short Term memory: cbaca

Iteration   | Memory   | Conflict Set | Rule Fired|
---  | --- | --- | ---
0| cbaca |1,2,3|1
1|cabca|2|2
2|acbac|1,3|3
3|abcac|2|2
4|abacc|1|1|
5|aabcc|halt|-|

### 8. Constraint Satisfaction Problem (CSP)

* are mathematical problems where one must find states or objects that satisfy a number of constraints or criteria.
* A Constraint Satisfaction problem is characterized by:
    1. A set of Variables {x1,x2, ... xn} For each variable xi a Domain Di with a possible value for that variable.
    2. A set of Constraints i.e. the relations that are assumed to be hold between the values of the variables. These relation can be given intentionally or extensionally.
* the constraint satisfaction problem is to find, for each i form 1 to n, a value in Di for xi such that all constraints are satisfied.

Example 1: 8 queen problem, All diff number

## Search

### Search strategies

Evaluated along following dimensions:

1. Completeness
2. Time Complexity
3. Space Complexity
4. Optimality

Time and space complexity are measured in terms of :

* b - maximum branching factor (may be infinite)
* d - depth of the least cost solution
* m - maximum depth of the state space (may be infinite)

## Search Types

Depending upon the basis of information available to the agent, search strategy can be classified into two types:

1. Blind Search
2. Heuristic Search

## 1. Blind Search

* no additional information
* only generate successors and distinguish goal state form non-goal state.
* Strategy has no idea of path cost or search cost form initial to goal node.
* Only information available is problem definition.
* less effective than informed search.

Various Blind Search

### 1. Breadth First Search

* root first and then successor expanded.
* Fringe is implemented as a FIFO queue.
* Time: b^(d+1), Space: b^(d+1)

### 2. Uniform Cost Search

* BFS finds the shallowest goal but it is not always optimal when the path cost between the nodes are different.
* UCS is used when travelling cost from one node to another is available.
* UCS always expands the lowest cost node on fringe.
* Fringe is implemented in priority queue.
* When the edge cost are all same UCS will yield the same traversal pattern as BFS
* BFS is just UCS with g(n) = DEPTH(n)
* Time: b^d, Space: b^d

### 3. Depth First Search

* always extracts one of the nodes at the deepest level of the tree only when search hits a dead end does the search go back and extract the node at the shallowest level.
* Unexplored successor are palced on stack until fully explored.
* Fringe is implemented as FILO stack
* Time: b^m, Space: bm

### 4. Depth Limit Search

* a limit l
* Time: b^l, Space: bl

### Iterative Depth Search

* limit 0,1,2 ... m
* Time: b^d, Space: bd

## Bidirectional Search

* Time: b^d/2, Space: b^d/2

## 2. Heuristic search

* Strategies tha know whether a non-goal is "more-promising" than the other.
* additional information.
* The idea is to generate a domain specific heuristic function h(n).
* h(n) guesses the cost of getting to the goal from node n.
* heuristic increases the efficiency of search.

## 3. Admissible Heuristic

An admissible heuristic never over estimates the cost to reach the goal ie it is optimistic.

if h(n) = Estimated cost to reach from node n to goal node and h*(n) - Actual cost to reach goal node form n then :

    h(n) <= h*(n)

Formulating Admissible heuristic:

* n is a node
* h is a heuristic
* h(n) is cost indicated by h to reach a goal node form n
* c(n) is the actual cost to reach goal from n
* h is admissible if:

        For ALl h(n) <= C(n)

### Theorem

>> The A* is optimal if the heuristic is Admissible or If h(n) is admissible, A* using tree search is optimal

Suppose some sub-optimal goal has been generated and is in the fringe. Let n be an unexpanded node in fringe such that n is on the shortest path to the optimal goal G and C* be the cost of optimal goal.

    Here,

    f(G2) = h (G2) + g(G2)
          = g(G2) [h(G2) = 0]
    f(G2) > c* (since sub optimal goal)
    f(n) = h(n) + g(n)
        <= c*
    Since, h(n) is admissible it doesn't over estimates the the cost of completing the solution path.

    Now,
    f(n) <= c* < f(G2)

    Since f(G2) > f(n) A* will never select G2 for expansion

    Thus A* gives optimal solution when heuristic is admissible.

### Consistent Heuristic

A heuristic is said to be consistent if for any node N and andy successor N' of N, estimated cost to reach the goal node is less than the sum of step cost from N to N' and estimated cost from N' to goal Node i.e

    h(N) <= d(N,N') + h(N')

>> Theorem: If h(n) is consistent, then the values of f(n) along the path are non decreasing.

    Suppose n' is successor of n as show in figure then,

    g(n') = g(n) + d(n,n')

    we know,

    f(n') = g(n') + h(n')
          = g(n)  + d(n,n') + h(n')
    form definition of consistent heuristic

    h(n) <= d(n,n') + h(n')

    from the above two,

    g(n) + d(n,n') + h(n') >= g(n) + h(n)

    Therefore,
    f(n') >= f(n)

    Thus, f(n) is non decreasing.
