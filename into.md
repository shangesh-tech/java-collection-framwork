# 1️⃣ What is the Java Collection Framework?

The **Java Collections Framework** is a set of **classes and interfaces** used to **store and manipulate groups of objects**.

Example problem:

You want to store:

* list of students
* unique IDs
* key-value pairs
* sorted numbers

Instead of writing your own data structures, Java provides them.

---

# 2️⃣ Structure of Collection Framework

Main hierarchy:

```
Iterable
   |
Collection
   |
-----------------------------
|            |              |
List         Set           Queue
```

Another branch:

```
Map   (separate interface)
```

So the **4 major parts** are:

1️⃣ List
2️⃣ Set
3️⃣ Queue
4️⃣ Map

---

# 3️⃣ LIST (Ordered + Duplicates allowed)

Important classes:

* **ArrayList**
* **LinkedList**
* **Vector**
* **Stack**

---

# 4️⃣ ARRAYLIST (Most Important)

### Characteristics

✔ Ordered
✔ Allows duplicates
✔ Fast random access
❌ Slow insert/delete in middle

---

## Example Code

```java
import java.util.*;

public class Demo {
    public static void main(String[] args) {

        ArrayList<Integer> list = new ArrayList<>();

        list.add(10);
        list.add(20);
        list.add(30);
        list.add(20);

        System.out.println(list);

        list.remove(1);

        System.out.println(list);
        System.out.println(list.get(1));
    }
}
```

---

# Dry Run

### Step 1

```
ArrayList<Integer> list = new ArrayList<>();
```

list = `[ ]`

---

### Step 2

```
list.add(10)
```

```
[10]
```

---

### Step 3

```
list.add(20)
```

```
[10, 20]
```

---

### Step 4

```
list.add(30)
```

```
[10, 20, 30]
```

---

### Step 5

```
list.add(20)
```

duplicates allowed

```
[10, 20, 30, 20]
```

---

### Step 6

```
list.remove(1)
```

removes index 1

```
[10, 30, 20]
```

---

### Step 7

```
list.get(1)
```

Output

```
30
```

---

# Important ArrayList Methods

| Method     | Work    |
| ---------- | ------- |
| add()      | insert  |
| remove()   | delete  |
| get()      | access  |
| set()      | replace |
| size()     | length  |
| contains() | search  |

---

# Real Example Problem

Find duplicate numbers.

```
Input:
[1,2,3,2,4]
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(1);
list.add(2);
list.add(3);
list.add(2);
list.add(4);

for(int i=0;i<list.size();i++){
    for(int j=i+1;j<list.size();j++){
        if(list.get(i)==list.get(j)){
            System.out.println(list.get(i));
        }
    }
}
```

Output

```
2
```

---

# When to use ArrayList?

Use when:

✔ frequent reading
✔ dynamic array
✔ random access

Example problems:

* store elements
* dynamic arrays
* graph adjacency list
* DFS / BFS storage

---

# 5️⃣ LINKEDLIST

Class:

**LinkedList**

Structure:

```
[Data | Address] -> [Data | Address] -> [Data | Address]
```

---

## Code Example

```java
import java.util.*;

public class Demo {
    public static void main(String[] args) {

        LinkedList<Integer> list = new LinkedList<>();

        list.add(10);
        list.add(20);
        list.addFirst(5);
        list.addLast(30);

        System.out.println(list);
    }
}
```

Output

```
[5, 10, 20, 30]
```

---

# Dry Run

Step 1

```
[]
```

Step 2

```
add(10)
```

```
10
```

Step 3

```
add(20)
```

```
10 -> 20
```

Step 4

```
addFirst(5)
```

```
5 -> 10 -> 20
```

Step 5

```
addLast(30)
```

```
5 -> 10 -> 20 -> 30
```

---

# When to use LinkedList

✔ frequent insertion
✔ frequent deletion

Example:

* queue
* browser history
* music playlist

---

# 6️⃣ SET (Unique Elements)

Classes:

* **HashSet**
* **LinkedHashSet**
* **TreeSet**

---

# HashSet Example

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        HashSet<Integer> set = new HashSet<>();

        set.add(10);
        set.add(20);
        set.add(10);

        System.out.println(set);
    }
}
```

Output

```
[10,20]
```

duplicate removed automatically.

---

# When to use HashSet

✔ remove duplicates
✔ fast searching

Example problems:

* find unique elements
* duplicates detection
* visited nodes in graphs

---

# 7️⃣ MAP (Key-Value)

Classes:

* **HashMap**
* **LinkedHashMap**
* **TreeMap**

---

# HashMap Example

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        HashMap<Integer,String> map = new HashMap<>();

        map.put(1,"Java");
        map.put(2,"Python");
        map.put(3,"C++");

        System.out.println(map.get(2));
    }
}
```

Output

```
Python
```

---

# Dry Run

```
put(1,"Java")
```

```
1 -> Java
```

```
put(2,"Python")
```

```
1 -> Java
2 -> Python
```

```
get(2)
```

Output

```
Python
```

---

# When to use HashMap

✔ frequency counting
✔ mapping
✔ caching

Example problems:

* Two Sum
* Anagram
* Word frequency

---

# Example LeetCode Problem

**Two Sum**

Solution using HashMap:

```java
public int[] twoSum(int[] nums, int target) {

    HashMap<Integer,Integer> map = new HashMap<>();

    for(int i=0;i<nums.length;i++){

        int complement = target - nums[i];

        if(map.containsKey(complement)){
            return new int[]{map.get(complement),i};
        }

        map.put(nums[i],i);
    }

    return new int[]{};
}
```

---

# How to Decide Which Collection to Use

| Problem Type           | Use        |
| ---------------------- | ---------- |
| Dynamic array          | ArrayList  |
| frequent insert/delete | LinkedList |
| unique elements        | HashSet    |
| sorted elements        | TreeSet    |
| key-value pairs        | HashMap    |
| sorted map             | TreeMap    |

