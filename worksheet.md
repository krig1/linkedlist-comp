# A3 Worksheet: Design Document for the Linked List

**Name: Kritin Gangwar**
**Onyen: krig**

Six sections, 15 points. Fill this in **before** you write any code. It is a design document, so it says what your methods must do and what must stay true, not how you will write them. Everything you need is in `README.md`. Keep it short: the whole document should fit on about one page. Write your answers directly under each prompt.

---

## 1. The problem in your own words (2 points)

In two or three sentences, describe the problem this assignment asks you to solve. Say what the six new methods let a program do with a list of whole numbers, and whether they build new lists or change the ones they are given.

```
The assignment adds methods into a linked list of whole numbers: putting a list in front of one, removing an element at a given index, checking whether two lists are equal, removing duplicates, reversing it, and interleaving. Every method works on the list it's called rather than building a new one.
```

---

## 2. Operations (3 points)

For each method you will write, describe in a few words what it is responsible for. Then say which of the list's **first node**, **last node**, and **size** the method can change, and in what situation. If it can change none of them, write "none". For the two merge methods, also say what state `list2` is left in.

| Method | What it is responsible for                                     | Which of first node / last node / size it can change, and when                                           |
|---|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| `simpleMerge` | Move list2's nodes to the front of the list, then clear list2  | First node: whenever list2 is non-empty. Last node: when the list is empty. Size: grows by list2's size. |
| `removeAtIndex` | Unlink the node at index i                                     | First node: when i == 0. Last: hen i == size -. Size: drops by 1 on every valid call.                    |
| `isEqual` | Return true when both lists have same size and values in order | None                                                                                                     |
| `removeRepeats` | In a sortest list, keep only one node for each value.          | First: never. Last: when the list ends in repeats. Size: drops by the number of nodes removed            |
| `reverse` | Reverse the order of the nodes.                                | First and last: they swap when size >=2. Size: never                                                     |
| `merge` | Interleave list2 into this list                                | First: become list2' first node whenever it's not empty. Last: never. Size: grows by list2's ize.        |

---

## 3. Data structure and justification (2 points)

This assignment uses a singly linked list that keeps a reference to both its first node and its last node. In one sentence, justify a linked list over an array-backed list (like the dynamic array from L11) for the work in Tasks 1 and 6. In a second sentence, explain what keeping a reference to the **last** node gives the class, and name one method, either provided or one of yours, that would have to do more work without it.

```
Tasks 1 and 6 relink nodes that already exist so inserting randonmly would cause a pointer change, but an array lacked list owuld have to shift every element after the insertion. Keeping a rference to o the last node lets the clas reach the end in constant time. 
```

---

## 4. Class invariant (3 points)

State the invariant the `LinkedList` class must maintain: what is always true about `_head`, `_tail`, and `_size` whenever no method is in the middle of running. Your answer should cover an empty list and a non-empty list, and it should say how `_size` relates to the nodes actually in the list.

```
When the list is empty, _head and _tail are null and _size is 0. When list is non empty, _head is the first node, and getNext() from _head reaches every node once and ends at _tail. _tail.getNext() is null, and _head == _tail only when there's just one node. 
```

---

## 5. Three edge cases (3 points)

List three edge cases where a first attempt at one of your methods is likely to go wrong. Use at least two different methods, and don't reuse the main examples from the README. For each one, give the exact input (the list, plus `list2` or the index where one applies) and the correct result, including anything that must change about the first node, the last node, or the size.

| Method        | Input            | Correct result                                                                                    |
|---------------|------------------|---------------------------------------------------------------------------------------------------|
| removeAtIndex | List 7, index 0  | empty list. first and last node both null, size 0.                                                |
| removeRepeats | List 2 -> 4 -> 4 | 2->4. First node is unchanged; last is the first 4 and its next is null and size goes from 3 to 2 |
| reverse       | List 1->2        | 2 -> 1. First is the old last node, last node is the old first node. Size stays 2.                |

---

## 6. Test strategy (2 points)

In two or three sentences, describe how you will check each method before you submit to the autograder. Say what you will look at after each call besides the printed contents of the list, and where your edge cases from section 5 come in.

```
I'll run the examples in Main and compare the outputs. After each call I'll also print size() and check it. For removeatIndex I will also wrap an out of range call in try/catch to make sure it throws the right exception.
```

---

## Submitting

Turn this in with your answers as a `.md` file on Gradescope. The code goes to Gradescope separately; see `README.md`.
