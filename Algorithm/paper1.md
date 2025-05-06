# MCA-204 Algorithm Design Examination Answers

## Question 1
### a) Discuss about the ADT binary tree, its implementation and explain with an example.

**Answer:**
An Abstract Data Type (ADT) Binary Tree is a hierarchical data structure where each node has at most two children, called the left child and right child. The ADT binary tree defines operations that can be performed on the tree without specifying how these operations are implemented.

**Key Properties of Binary Tree:**
- Every node has at most two children (left and right)
- Each node contains one data element
- The left subtree of a node contains only values less than the node's value (for Binary Search Tree)
- The right subtree of a node contains only values greater than the node's value (for Binary Search Tree)
- There is exactly one path from the root to any node

**Types of Binary Trees:**
1. **Full Binary Tree**: Every node has either 0 or 2 children
2. **Complete Binary Tree**: All levels are filled except possibly the last level, which is filled from left to right
3. **Perfect Binary Tree**: All internal nodes have two children and all leaf nodes are at the same level
4. **Balanced Binary Tree**: The height of the left and right subtrees of any node differ by at most one

**Implementation Methods:**

1. **Array-based Implementation:**
   - For a node at index i:
   - Left child is stored at index 2i + 1
   - Right child is stored at index 2i + 2
   - Parent is stored at index (i-1)/2 (floor value)
   
   **Advantages:**
   - Easy to implement
   - No need for pointers
   - Random access to nodes
   
   **Disadvantages:**
   - Fixed size
   - May waste space for sparse trees
   - Insertion and deletion operations are difficult

2. **Linked Implementation:**
   - Each node contains:
     - Data field
     - Pointer to left child
     - Pointer to right child
   
   **Advantages:**
   - Dynamic size
   - Efficient insertion and deletion
   - No wasted space
   
   **Disadvantages:**
   - Extra memory for storing pointers
   - No random access to nodes

**Example of Node Structure in C:**
```java
class Node {
    int data;
    Node left;
    Node right;
    
    // Constructor to create a new node
    public Node(int value) {
        data = value;
        left = null;
        right = null;
    }
}
```

**Example Binary Tree:**
```
       50
      /  \
    30    70
   /  \   /  \
  20  40 60  80
```

**Creating this tree in code:**
```java
// Create the root node with value 50
Node root = new Node(50);

// Create and link level 1 nodes
root.left = new Node(30);
root.right = new Node(70);

// Create and link level 2 nodes
root.left.left = new Node(20);
root.left.right = new Node(40);
root.right.left = new Node(60);
root.right.right = new Node(80);
```

**Common Operations on Binary Trees:**

1. **Tree Traversal Methods:**
   - **In-order (Left, Root, Right)**: For the example tree, output would be: 20, 30, 40, 50, 60, 70, 80
   - **Pre-order (Root, Left, Right)**: For the example tree, output would be: 50, 30, 20, 40, 70, 60, 80
   - **Post-order (Left, Right, Root)**: For the example tree, output would be: 20, 40, 30, 60, 80, 70, 50
   - **Level-order (Breadth-first)**: For the example tree, output would be: 50, 30, 70, 20, 40, 60, 80

2. **Other Operations:**
   - Insertion of a node
   - Deletion of a node
   - Searching for a value
   - Finding minimum/maximum value
   - Finding height of the tree
   - Counting number of nodes

**Applications of Binary Trees:**
- Binary Search Trees for efficient searching, insertion, and deletion
- Expression trees for representing mathematical expressions
- Huffman coding trees for data compression
- Decision trees in machine learning
- Heap implementation for priority queues

### b) What is a circular linked list. What are the different operations performed on it? Explain with an example.

**Answer:**
A circular linked list is a variation of linked list data structure where the last node points back to the first node (head), creating a closed loop. Unlike a regular linked list which ends with a NULL pointer, a circular list allows continuous traversal through all nodes without stopping.

**Types of Circular Linked Lists:**

1. **Singly Circular Linked List:** 
   - Each node contains data and a next pointer
   - Last node's next pointer points to the first node
   - Traversal can only be done in forward direction

2. **Doubly Circular Linked List:**
   - Each node contains data, next pointer, and previous pointer
   - Last node's next points to first node
   - First node's previous points to last node
   - Traversal can be done in both forward and backward directions

**Memory Representation of Singly Circular Linked List:**
```
    +-----+------+      +-----+------+      +-----+------+
    | 10  | next |----->| 20  | next |----->| 30  | next |
    +-----+------+      +-----+------+      +-----+------+
        ^                                        |
        |                                        |
        +----------------------------------------+
```

**Operations on Circular Linked Lists:**

1. **Insertion Operations:**

   a) **Insert at the Beginning:**
   ```java
   public Node insertAtBeginning(Node head, int value) {
       // Create a new node
       Node newNode = new Node(value);
       
       // If list is empty
       if (head == null) {
           newNode.next = newNode;  // Point to itself
           return newNode;
       }
       
       // Find the last node
       Node last = head;
       while (last.next != head) {
           last = last.next;
       }
       
       // Link the new node
       newNode.next = head;
       last.next = newNode;
       
       return newNode;  // New node becomes the head
   }
   ```

   b) **Insert at the End:**
   ```java
   public Node insertAtEnd(Node head, int value) {
       // Create a new node
       Node newNode = new Node(value);
       
       // If list is empty
       if (head == null) {
           newNode.next = newNode;  // Point to itself
           return newNode;
       }
       
       // Find the last node
       Node last = head;
       while (last.next != head) {
           last = last.next;
       }
       
       // Link the new node
       last.next = newNode;
       newNode.next = head;
       
       return head;  // Head remains the same
   }
   ```

   c) **Insert at a Specific Position:**
   ```java
   public Node insertAtPosition(Node head, int value, int position) {
       // If list is empty or position is 1, insert at beginning
       if (head == null || position == 1) {
           return insertAtBeginning(head, value);
       }
       
       // Create a new node
       Node newNode = new Node(value);
       
       // Traverse to the node just before the position
       Node current = head;
       for (int i = 1; i < position - 1; i++) {
           current = current.next;
           // If position exceeds list length, insert at end
           if (current == head) {
               return insertAtEnd(head, value);
           }
       }
       
       // Link the new node
       newNode.next = current.next;
       current.next = newNode;
       
       return head;
   }
   ```

2. **Deletion Operations:**

   a) **Delete from the Beginning:**
   ```java
   public Node deleteFromBeginning(Node head) {
       // If list is empty
       if (head == null) {
           return null;
       }
       
       // If only one node
       if (head.next == head) {
           return null;
       }
       
       // Find the last node
       Node last = head;
       while (last.next != head) {
           last = last.next;
       }
       
       // Update head and link last node to new head
       Node newHead = head.next;
       last.next = newHead;
       
       return newHead;
   }
   ```

   b) **Delete from the End:**
   ```java
   public Node deleteFromEnd(Node head) {
       // If list is empty
       if (head == null) {
           return null;
       }
       
       // If only one node
       if (head.next == head) {
           return null;
       }
       
       // Find the second last node
       Node current = head;
       while (current.next.next != head) {
           current = current.next;
       }
       
       // Update the links
       current.next = head;
       
       return head;
   }
   ```

3. **Traversal Operation:**
   ```java
   public void traverseCircularList(Node head) {
       // If list is empty
       if (head == null) {
           System.out.println("List is empty");
           return;
       }
       
       Node current = head;
       do {
           System.out.print(current.data + " -> ");
           current = current.next;
       } while (current != head);
       
       System.out.println("(Back to head)");
   }
   ```

4. **Searching Operation:**
   ```java
   public boolean search(Node head, int key) {
       // If list is empty
       if (head == null) {
           return false;
       }
       
       Node current = head;
       do {
           if (current.data == key) {
               return true;
           }
           current = current.next;
       } while (current != head);
       
       return false;
   }
   ```

**Example of Complete Singly Circular Linked List Implementation:**

```java
class Node {
    int data;
    Node next;
    
    public Node(int value) {
        data = value;
        next = null;
    }
}

class CircularLinkedList {
    private Node head;
    
    public CircularLinkedList() {
        head = null;
    }
    
    // Insert at the beginning
    public void insertAtBeginning(int value) {
        Node newNode = new Node(value);
        
        if (head == null) {
            head = newNode;
            newNode.next = head;
        } else {
            Node last = head;
            while (last.next != head) {
                last = last.next;
            }
            
            newNode.next = head;
            last.next = newNode;
            head = newNode;
        }
    }
    
    // Display the list
    public void display() {
        if (head == null) {
            System.out.println("List is empty");
            return;
        }
        
        Node temp = head;
        do {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        } while (temp != head);
        
        System.out.println("(Back to head)");
    }
}

// Example usage
public class Main {
    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();
        
        list.insertAtBeginning(30);
        list.insertAtBeginning(20);
        list.insertAtBeginning(10);
        
        System.out.println("Circular Linked List:");
        list.display();  // Output: 10 -> 20 -> 30 -> (Back to head)
    }
}
```

**Advantages of Circular Linked List:**
1. Any node can be starting point
2. Useful for applications requiring round-robin scheduling
3. We can traverse the whole list starting from any point
4. Implementation of advanced data structures like Fibonacci Heap
5. Used in implementations of queue

**Disadvantages:**
1. Complexity increases as the last node needs to point to the first
2. Special care needed while traversing to avoid infinite loops
3. Slightly more complex insertions and deletions

**Applications of Circular Linked List:**
1. Implementation of advanced data structures like Fibonacci Heap
2. CPU scheduling in operating systems
3. Multiplayer games where players take turns
4. Managing computer resources and round-robin scheduling
5. Audio/Video streaming, to repeat the playlist

7. Repeat steps 3-6 until (V-1) edges are added to the MST

**Java Implementation of Kruskal's Algorithm:**
```java
class Edge implements Comparable<Edge> {
    int src, dest, weight;
    
    // Constructor
    public Edge(int src, int dest, int weight) {
        this.src = src;
        this.dest = dest;
        this.weight = weight;
    }
    
    // Comparator function used for sorting edges
    public int compareTo(Edge compareEdge) {
        return this.weight - compareEdge.weight;
    }
}

class Subset {
    int parent, rank;
    
    public Subset(int parent, int rank) {
        this.parent = parent;
        this.rank = rank;
    }
}

public class KruskalAlgorithm {
    int V, E;    // V -> number of vertices, E -> number of edges
    Edge[] edges;    // Collection of all edges
    
    // Constructor
    public KruskalAlgorithm(int v, int e) {
        V = v;
        E = e;
        edges = new Edge[E];
        for (int i = 0; i < e; ++i) {
            edges[i] = new Edge(0, 0, 0);
        }
    }
    
    // A utility function to find set of an element i (uses path compression)
    int find(Subset[] subsets, int i) {
        // Find root and make root as parent of i (path compression)
        if (subsets[i].parent != i) {
            subsets[i].parent = find(subsets, subsets[i].parent);
        }
        return subsets[i].parent;
    }
    
    // A function that does union of two sets (uses union by rank)
    void union(Subset[] subsets, int x, int y) {
        int xroot = find(subsets, x);
        int yroot = find(subsets, y);
        
        // Attach smaller rank tree under root of high rank tree
        if (subsets[xroot].rank < subsets[yroot].rank) {
            subsets[xroot].parent = yroot;
        } else if (subsets[xroot].rank > subsets[yroot].rank) {
            subsets[yroot].parent = xroot;
        } else {
            // If ranks are same, make one as root and increment its rank
            subsets[yroot].parent = xroot;
            subsets[xroot].rank++;
        }
    }
    
    // Main function to construct MST using Kruskal's algorithm
    void kruskalMST() {
        Edge[] result = new Edge[V];  // Will store the resultant MST
        int e = 0;  // Index for result[]
        int i = 0;  // Index for sorted edges
        
        // Initialize result
        for (i = 0; i < V; ++i) {
            result[i] = new Edge(0, 0, 0);
        }
        
        // Sort all edges in non-decreasing order of their weight
        Arrays.sort(edges);
        
        // Create V subsets with single elements
        Subset[] subsets = new Subset[V];
        for (i = 0; i < V; ++i) {
            subsets[i] = new Subset(i, 0);
        }
        
        i = 0;  // Reset index for sorted edges
        
        // Number of edges to be taken is equal to V-1
        while (e < V - 1 && i < E) {
            // Pick the smallest edge
            Edge next_edge = edges[i++];
            
            int x = find(subsets, next_edge.src);
            int y = find(subsets, next_edge.dest);
            
            // If including this edge doesn't cause cycle, include it in result
            if (x != y) {
                result[e++] = next_edge;
                union(subsets, x, y);
            }
            // Else discard the edge
        }
        
        // Print the constructed MST
        System.out.println("Following are the edges in the constructed MST");
        int minimumCost = 0;
        for (i = 0; i < e; ++i) {
            System.out.println(result[i].src + " -- " + result[i].dest + " == " + result[i].weight);
            minimumCost += result[i].weight;
        }
        System.out.println("Minimum Cost Spanning Tree: " + minimumCost);
    }
}
```

**Example Application of Both Algorithms:**

Let's consider the following graph to find the MST:
```
   (0)   9   (1)
    |  \    / |
    4    6    2
    |      \  |
   (3)   1   (2)
    |  \    / |
    3    5    7
    |      \  |
   (5)   8   (4)
```

**Using Prim's Algorithm:**
1. Start with vertex 0
2. Available edges: (0,1) with weight 9, (0,3) with weight 4, (0,2) with weight 6
3. Choose (0,3) as it has minimum weight
4. MST so far: {(0,3)}
5. Available edges: (0,1) with weight 9, (0,2) with weight 6, (3,5) with weight 3, (3,4) with weight 5
6. Choose (3,5) as it has minimum weight
7. MST so far: {(0,3), (3,5)}
8. Available edges: (0,1) with weight 9, (0,2) with weight 6, (3,4) with weight 5, (5,4) with weight 8
9. Choose (3,4) as it has minimum weight
10. MST so far: {(0,3), (3,5), (3,4)}
11. Available edges: (0,1) with weight 9, (0,2) with weight 6, (4,2) with weight 7, (5,4) with weight 8
12. Choose (0,2) as it has minimum weight
13. MST so far: {(0,3), (3,5), (3,4), (0,2)}
14. Available edges: (0,1) with weight 9, (2,1) with weight 2, (4,2) with weight 7, (5,4) with weight 8
15. Choose (2,1) as it has minimum weight
16. MST so far: {(0,3), (3,5), (3,4), (0,2), (2,1)}

Final MST edges: {(0,3), (3,5), (3,4), (0,2), (2,1)}
Total MST weight: 4 + 3 + 5 + 6 + 2 = 20

**Using Kruskal's Algorithm:**
1. Sort all edges by weight: (3,5) with weight 3, (2,1) with weight 2, (0,3) with weight 4, (3,4) with weight 5, (0,2) with weight 6, (4,2) with weight 7, (5,4) with weight 8, (0,1) with weight 9
2. Pick (2,1) with weight 2: Add to MST
3. Pick (3,5) with weight 3: Add to MST
4. Pick (0,3) with weight 4: Add to MST
5. Pick (3,4) with weight 5: Add to MST
6. Pick (0,2) with weight 6: Add to MST (we have added 5 edges which is V-1)

Final MST edges: {(2,1), (3,5), (0,3), (3,4), (0,2)}
Total MST weight: 2 + 3 + 4 + 5 + 6 = 20

Both algorithms produce an MST with the same total weight, though the specific edges might differ if there are multiple MSTs with the same total weight.

**Comparison between Prim's and Kruskal's Algorithms:**

1. **Time Complexity:**
   - Prim's Algorithm: O(V²) with simple array, O(E log V) with binary heap or Fibonacci heap
   - Kruskal's Algorithm: O(E log E) or O(E log V) since E can be at most V²

2. **Suitable for:**
   - Prim's Algorithm: Dense graphs (more edges)
   - Kruskal's Algorithm: Sparse graphs (fewer edges)

3. **Implementation:**
   - Prim's Algorithm: Requires priority queue or min-heap
   - Kruskal's Algorithm: Requires sorting and disjoint-set data structure

4. **Approach:**
   - Prim's Algorithm: Grows the MST by adding vertices
   - Kruskal's Algorithm: Grows the MST by adding edges

### iii) Illustrate BFS and DFS for the following graph.

**Answer:**

Breadth-First Search (BFS) and Depth-First Search (DFS) are two fundamental graph traversal algorithms.

**Breadth-First Search (BFS):**

BFS explores all neighbors at the present depth prior to moving on to nodes at the next depth level. It uses a queue data structure for traversal.

**Steps in BFS:**
1. Start at a chosen source vertex
2. Visit all its unvisited adjacent vertices
3. For each adjacent vertex, visit all its unvisited adjacent vertices
4. Continue until all vertices are visited

**Java Implementation of BFS:**
```java
public void BFS(int startVertex, int adjacencyMatrix[][]) {
    int numVertices = adjacencyMatrix.length;
    
    // Mark all vertices as not visited (by default set as false)
    boolean[] visited = new boolean[numVertices];
    
    // Create a queue for BFS
    LinkedList<Integer> queue = new LinkedList<Integer>();
    
    // Mark the current node as visited and enqueue it
    visited[startVertex] = true;
    queue.add(startVertex);
    
    System.out.print("Breadth First Traversal starting from vertex " + startVertex + ": ");
    
    while (!queue.isEmpty()) {
        // Dequeue a vertex from queue and print it
        startVertex = queue.poll();
        System.out.print(startVertex + " ");
        
        // Get all adjacent vertices of the dequeued vertex
        // If an adjacent has not been visited, then mark it visited and enqueue it
        for (int i = 0; i < numVertices; i++) {
            if (adjacencyMatrix[startVertex][i] == 1 && !visited[i]) {
                visited[i] = true;
                queue.add(i);
            }
        }
    }
    System.out.println();
}
```

**Depth-First Search (DFS):**

DFS explores as far as possible along each branch before backtracking. It uses a stack data structure (or recursion) for traversal.

**Steps in DFS:**
1. Start at a chosen source vertex
2. Visit any unvisited adjacent vertex
3. Continue from that vertex, visiting its unvisited adjacent vertices
4. Backtrack when no unvisited adjacent vertices are available
5. Continue until all vertices are visited

**Java Implementation of DFS:**
```java
// DFS traversal from a given source vertex
public void DFS(int startVertex, boolean[] visited, int adjacencyMatrix[][]) {
    // Mark the current node as visited and print it
    visited[startVertex] = true;
    System.out.print(startVertex + " ");
    
    // Recur for all the vertices adjacent to this vertex
    for (int i = 0; i < adjacencyMatrix.length; i++) {
        if (adjacencyMatrix[startVertex][i] == 1 && !visited[i]) {
            DFS(i, visited, adjacencyMatrix);
        }
    }
}

// Wrapper function for DFS traversal
public void DFSTraversal(int startVertex, int adjacencyMatrix[][]) {
    int numVertices = adjacencyMatrix.length;
    
    // Mark all vertices as not visited (by default set as false)
    boolean[] visited = new boolean[numVertices];
    
    System.out.print("Depth First Traversal starting from vertex " + startVertex + ": ");
    
    // Call the recursive helper function
    DFS(startVertex, visited, adjacencyMatrix);
    
    System.out.println();
}
```

**Example of BFS and DFS on a Graph:**

Let's consider the following undirected graph:
```
    1 --- 2
    |     |
    |     |
    4 --- 3
```

Adjacency matrix representation:
```
    0 1 0 1
    1 0 1 0
    0 1 0 1
    1 0 1 0
```

**BFS Traversal (starting from vertex 1):**
1. Visit vertex 1, mark it as visited
2. Visit all adjacent vertices of 1: 2 and 4
3. Visit all adjacent vertices of 2: 3
4. Visit all adjacent vertices of 4: 3 (already visited)
5. All vertices have been visited

BFS traversal: 1 2 4 3

**DFS Traversal (starting from vertex 1):**
1. Visit vertex 1, mark it as visited
2. Visit any adjacent vertex of 1, say 2
3. Visit any adjacent vertex of 2, say 3
4. Visit any adjacent vertex of 3, say 4
5. All vertices have been visited

DFS traversal: 1 2 3 4

**Applications of BFS:**
1. Shortest path in an unweighted graph
2. Peer-to-peer networks
3. Web crawlers
4. Social networking search
5. GPS navigation systems
6. Broadcasting in networks

**Applications of DFS:**
1. Topological sorting
2. Detecting cycles in a graph
3. Path finding
4. Solving puzzles like mazes
5. Connected components
6. Strongly connected components

**Time and Space Complexity:**
- Time Complexity (both BFS and DFS): O(V + E) where V is the number of vertices and E is the number of edges
- Space Complexity:
  - BFS: O(V) for the queue
  - DFS: O(V) for the recursion stack or explicit stack

## Question 4
### a) Illustrate merge sort algorithm and discuss time complexity for the following data: 78, 32, 42, 62, 98, 12, 34, 83

**Answer:**
Merge Sort is an efficient, stable, comparison-based, divide and conquer sorting algorithm. It divides the input array into two halves, recursively sorts them, and then merges the sorted halves.

**Key Features of Merge Sort:**
- Stable sorting algorithm (preserves the relative order of equal elements)
- Guaranteed O(n log n) time complexity regardless of input
- Not an in-place sorting algorithm (requires extra space for merging)

**Merge Sort Algorithm:**
1. **Divide**: Divide the unsorted list into two sublists of about half the size
2. **Conquer**: Recursively sort both sublists
3. **Combine**: Merge the two sorted sublists to produce a single sorted list

**Java Implementation of Merge Sort:**
```java
public class MergeSort {
    // Merges two subarrays of arr[]
    // First subarray is arr[l..m]
    // Second subarray is arr[m+1..r]
    void merge(int arr[], int l, int m, int r) {
        // Find sizes of two subarrays to be merged
        int n1 = m - l + 1;
        int n2 = r - m;
        
        // Create temp arrays
        int L[] = new int[n1];
        int R[] = new int[n2];
        
        // Copy data to temp arrays
        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];
        
        // Merge the temp arrays
        
        // Initial indexes of first and second subarrays
        int i = 0, j = 0;
        
        // Initial index of merged subarray array
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }
        
        // Copy remaining elements of L[] if any
        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }
        
        // Copy remaining elements of R[] if any
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
    
    // Main function that sorts arr[l..r] using merge()
    void sort(int arr[], int l, int r) {
        if (l < r) {
            // Find the middle point
            int m = l + (r - l) / 2;
            
            // Sort first and second halves
            sort(arr, l, m);
            sort(arr, m + 1, r);
            
            // Merge the sorted halves
            merge(arr, l, m, r);
        }
    }
}
```

**Example: Sorting [78, 32, 42, 62, 98, 12, 34, 83] using Merge Sort**

Let's trace through the Merge Sort algorithm on the given array:

1. **Divide the array into halves:**
   - Left half: [78, 32, 42, 62]
   - Right half: [98, 12, 34, 83]

2. **Recursively divide the left half:**
   - Left quarter: [78, 32]
   - Right quarter: [42, 62]
   
3. **Recursively divide [78, 32]:**
   - [78] and [32]
   - Merge: [32, 78]
   
4. **Recursively divide [42, 62]:**
   - [42] and [62]
   - Merge: [42, 62]
   
5. **Merge [32, 78] and [42, 62]:**
   - Compare 32 and 42: Take 32
   - Compare 78 and 42: Take 42
   - Compare 78 and 62: Take 62
   - Remaining: 78
   - Result: [32, 42, 62, 78]

6. **Recursively divide the right half [98, 12, 34, 83]:**
   - Left quarter: [98, 12]
   - Right quarter: [34, 83]
   
7. **Recursively divide [98, 12]:**
   - [98] and [12]
   - Merge: [12, 98]
   
8. **Recursively divide [34, 83]:**
   - [34] and [83]
   - Merge: [34, 83]
   
9. **Merge [12, 98] and [34, 83]:**
   - Compare 12 and 34: Take 12
   - Compare 98 and 34: Take 34
   - Compare 98 and 83: Take 83
   - Remaining: 98
   - Result: [12, 34, 83, 98]

10. **Final merge: [32, 42, 62, 78] and [12, 34, 83, 98]**
    - Compare 32 and 12: Take 12
    - Compare 32 and 34: Take 32
    - Compare 42 and 34: Take 34
    - Compare 42 and 83: Take 42
    - Compare 62 and 83: Take 62
    - Compare 78 and 83: Take 78
    - Remaining: 83, 98
    - Result: [12, 32, 34, 42, 62, 78, 83, 98]

**Time Complexity Analysis of Merge Sort:**

1. **Best Case:** O(n log n)
   - Even when the array is already sorted, merge sort still divides the array and merges the results
   - The division takes O(log n) steps
   - Each division level requires O(n) operations to merge
   - Total: O(n log n)

2. **Average Case:** O(n log n)
   - The division process creates a tree of height O(log n)
   - Each level of the tree requires O(n) operations for merging
   - Total: O(n log n)

3. **Worst Case:** O(n log n)
   - Same as the best and average cases
   - This is a significant advantage over algorithms like QuickSort, which can degrade to O(n²)

**Space Complexity:**
- O(n) - requires additional space for the temporary arrays used during merging

**Advantages of Merge Sort:**
1. Guaranteed O(n log n) time complexity regardless of input data
2. Stable sorting algorithm (preserves order of equal elements)
3. Well-suited for external sorting (sorting data that doesn't fit in memory)
4. Parallelizable (can be divided into independent subtasks)

**Disadvantages of Merge Sort:**
1. Requires extra space O(n)
2. Not an in-place sorting algorithm
3. Slower than other algorithms for small datasets due to overhead
4. Not adaptive (doesn't take advantage of existing order)

**When to Use Merge Sort:**
1. When stability is required
2. When guaranteed O(n log n) performance is needed
3. For external sorting
4. For linked lists (can be implemented with O(1) extra space)

### b) Compute the optimal solution for knapsack problem using Greedy method. N = 3, M = 20, (p₁, p₂, p₃) = (25, 24, 15), (w₁, w₂, w₃) = (18, 15, 10).

**Answer:**
The Knapsack Problem is an optimization problem where we need to select items to maximize profit while keeping the total weight within a specified limit.

**Greedy Approach for Knapsack Problem:**
In the greedy approach, we select items based on a particular criterion, such as:
1. Highest profit first
2. Lowest weight first
3. Highest profit/weight ratio first (most efficient)

The third approach (profit/weight ratio) is typically the most effective greedy strategy.

**Given:**
- Number of items (N) = 3
- Maximum weight capacity (M) = 20
- Profits: (p₁, p₂, p₃) = (25, 24, 15)
- Weights: (w₁, w₂, w₃) = (18, 15, 10)

**Step 1: Calculate profit/weight ratio for each item**
- Item 1: ratio = 25/18 = 1.389
- Item 2: ratio = 24/15 = 1.600
- Item 3: ratio = 15/10 = 1.500

**Step 2: Sort items by profit/weight ratio in descending order**
- Item 2: ratio = 1.600, weight = 15, profit = 24
- Item 3: ratio = 1.500, weight = 10, profit = 15
- Item 1: ratio = 1.389, weight = 18, profit = 25

**Step 3: Start selecting items in order of decreasing ratio until the knapsack is full**
- Select Item 2: weight = 15, profit = 24
- Remaining capacity = 20 - 15 = 5
- Try to select Item 3: weight = 10 (doesn't fit completely)
- Take a fraction of Item 3: (5/10) = 0.5 or 50%
- Profit from fractional item = 15 * 0.5 = 7.5

**Step 4: Calculate total profit**
- Total profit = 24 + 7.5 = 31.5

**Java Implementation of Greedy Knapsack:**
```java
class Item {
    int profit;
    int weight;
    double ratio;  // profit/weight ratio
    
    public Item(int profit, int weight) {
        this.profit = profit;
        this.weight = weight;
        this.ratio = (double) profit / weight;
    }
}

public class GreedyKnapsack {
    public static double getMaxProfit(int[] profits, int[] weights, int capacity) {
        int n = profits.length;
        Item[] items = new Item[n];
        
        // Create items with profit and weight
        for (int i = 0; i < n; i++) {
            items[i] = new Item(profits[i], weights[i]);
        }
        
        // Sort items by profit/weight ratio in descending order
        Arrays.sort(items, new Comparator<Item>() {
            @Override
            public int compare(Item item1, Item item2) {
                return Double.compare(item2.ratio, item1.ratio);
            }
        });
        
        double totalProfit = 0;
        int remainingCapacity = capacity;
        
        // Greedy selection of items
        for (int i = 0; i < n; i++) {
            // If we can take the whole item
            if (remainingCapacity >= items[i].weight) {
                totalProfit += items[i].profit;
                remainingCapacity -= items[i].weight;
            } 
            // If we can take only a fraction of the item
            else {
                double fraction = (double) remainingCapacity / items[i].weight;
                totalProfit += items[i].profit * fraction;
                remainingCapacity = 0;
                break;  // Knapsack is full
            }
        }
        
        return totalProfit;
    }
    
    public static void main(String[] args) {
        int[] profits = {25, 24, 15};
        int[] weights = {18, 15, 10};
        int capacity = 20;
        
        double maxProfit = getMaxProfit(profits, weights, capacity);
        System.out.println("Maximum profit = " + maxProfit);
    }
}
```

**Limitations of Greedy Approach for Knapsack:**
1. The greedy approach doesn't always give the optimal solution for the 0-1 Knapsack problem (when we can either take an item or leave it, but can't take a fraction).
2. For the fractional Knapsack problem (where we can take fractions of items), the greedy approach is optimal.

**Summary:**
Using the greedy approach with profit/weight ratio for the given knapsack problem, we get:
- Take 100% of Item 2 (profit = 24, weight = 15)
- Take 50% of Item 3 (profit = 15 * 0.5 = 7.5, weight = 10 * 0.5 = 5)
- Total profit = 24 + 7.5 = 31.5

## Question 5
### a) Distinguish NP-hard and NP-complete problems.

**Answer:**
To understand the distinction between NP-hard and NP-complete problems, we first need to understand some basic complexity classes:

**Complexity Classes:**

1. **P (Polynomial Time):**
   - Problems that can be solved in polynomial time by a deterministic Turing machine
   - Examples: Sorting, Searching, Matrix Multiplication

2. **NP (Nondeterministic Polynomial Time):**
   - Problems whose solutions can be verified in polynomial time
   - Every problem in P is also in NP (P ⊆ NP)
   - Examples: Traveling Salesman Decision Problem, Boolean Satisfiability

3. **NP-hard:**
   - Problems that are at least as hard as the hardest problems in NP
   - May not be in NP themselves
   - If an NP-hard problem could be solved in polynomial time, then all NP problems could also be solved in polynomial time

4. **NP-complete:**
   - Problems that are both in NP and NP-hard
   - The "hardest" problems in NP

**Distinguishing Features:**

| Feature | NP-hard | NP-complete |
|---------|---------|-------------|
| Definition | At least as hard as the hardest problems in NP | Both in NP and NP-hard |
| Verification | May not be verifiable in polynomial time | Can be verified in polynomial time |
| Membership in NP | May not be in NP | Must be in NP |
| Reduction | All NP problems can be reduced to any NP-hard problem | All NP problems can be reduced to any NP-complete problem |
| Examples | Halting Problem, TSP Optimization | Boolean Satisfiability (SAT), Traveling Salesman Decision, Vertex Cover |

**Key Differences:**

1. **Membership in NP:**
   - NP-complete problems must be in NP (solutions can be verified in polynomial time)
   - NP-hard problems may or may not be in NP

2. **Relationship:**
   - All NP-complete problems are NP-hard, but not all NP-hard problems are NP-complete
   - NP-complete = NP ∩ NP-hard

3. **Decision vs. Optimization:**
   - Many NP-complete problems are decision problems (yes/no answers)
   - The optimization versions of these problems are often NP-hard

**Examples of NP-hard Problems:**
1. Halting Problem (not in NP)
2. Traveling Salesman Optimization Problem (find the shortest route)
3. Graph Coloring Optimization (minimize the number of colors)
4. Knapsack Optimization Problem (maximize value)

**Examples of NP-complete Problems:**
1. Boolean Satisfiability Problem (SAT)
2. Traveling Salesman Decision Problem (is there a route shorter than k?)
3. Hamiltonian Cycle Problem
4. Vertex Cover Problem
5. Subset Sum Problem
6. Graph Coloring Decision Problem (can we color with k colors?)

**The P vs. NP Problem:**
- One of the most important open problems in theoretical computer science
- Question: Is P = NP?
- If P = NP, all NP-complete (and thus all NP) problems could be solved in polynomial time
- Most researchers believe P ≠ NP, meaning NP-complete problems have no polynomial-time solutions

**Reductions:**
- A problem A is reducible to problem B if any instance of A can be transformed into an instance of B, with the transformation computable in polynomial time
- If problem A reduces to problem B and B is solvable in polynomial time, then A is also solvable in polynomial time
- NP-completeness is often proved through reduction from a known NP-complete problem

**Practical Implications:**
1. For NP-complete and NP-hard problems, we generally use:
   - Approximation algorithms
   - Heuristic approaches
   - Parameterized algorithms
   - Exponential algorithms that work efficiently on small inputs
2. Understanding whether a problem is NP-hard or NP-complete helps in choosing the right approach for solving it

### b) Explain amortized analysis with suitable example.

**Answer:**
Amortized analysis is a method for analyzing the time complexity of algorithms where the average performance over a sequence of operations is considered, rather than the worst-case cost of a single operation. It's particularly useful for data structures with operations that occasionally require much more time than normal, but rarely enough that the average time remains low.

**Key Concepts of Amortized Analysis:**

1. **Average Performance:** Instead of focusing on worst-case performance for each operation, it analyzes the average performance over a sequence of operations.

2. **Accounting Method:** Assigns different "costs" to different operations, overcharging some operations to compensate for others.

3. **Potential Method:** Uses a potential function to track the state of the data structure and distribute costs across operations.

4. **Aggregate Method:** Analyzes the total cost of a sequence of operations and divides by the number of operations.

**Three Common Methods of Amortized Analysis:**

1. **Aggregate Method:**
   - Calculate the total cost of n operations
   - Divide by n to get the amortized cost per operation
   - Useful when the pattern of expensive operations is regular

2. **Accounting Method:**
   - Assign an amortized cost to each operation
   - Some operations are "overcharged" (cost more than their actual cost)
  
# Data Structures and Algorithms - Exam Answers

## Question 5
### b) Explain amortized analysis with suitable example.

Amortized analysis helps us find the average time taken by operations over time, instead of looking at the worst case every time. It's like looking at your monthly budget instead of panicking about one expensive day.

**Simple explanation:** Some operations are costly but happen rarely. Amortized analysis spreads this cost over many operations to find the true average cost.

**Example: Growing Array**

Let's take a simple example:
- We start with an array of size 1
- This doubling costs time to copy all elements

When we add elements:
```
Initial array (size 1): [A]
Array is full, double size: [A, _]
Add B: [A, B]
Array is full, double size: [A, B, _, _]
Add C: [A, B, C, _]
Add D: [A, B, C, D]
Array is full, double size: [A, B, C, D, _, _, _, _]
...and so on
```

**Normal analysis:** 
- Basic add: fast (O(1))
- Resize operation: slow (O(n))
- Worst case is O(n)

**Amortized analysis:**
If we do many adds, most are cheap and only few are expensive.

For n operations:
- We resize after 1, 2, 4, 8... elements
- Total cost of all resize operations ≈ n
- So average cost per operation is O(1)

This is like saving a little extra money each day to pay for occasional big expenses.

## Question 6
### a) Discuss about the applications of Stacks and Queues.

**STACKS**

A stack works like a pile of plates - you can only take from the top (Last In, First Out).

**Applications of Stacks:**

1. **Function Calls in Programs**
   - When your program calls a function, it puts the return address on a stack
   - When the function finishes, it pops the address and knows where to go back

   ![Stack for Function Calls](stack_function_calls.png)

2. **Checking Expressions**
   - Used to check if brackets match in code: ( { [ ] } )
   - When you see an opening bracket, push it on stack
   - When you see a closing bracket, check if it matches the top of stack

3. **Undo Feature**
   - Programs store your actions on a stack
   - When you press "undo," they pop the last action
   
4. **Browser History**
   - Back button uses a stack to remember pages you visited
   - Each new page gets pushed on the stack

**QUEUES**

A queue works like a line of people waiting - first person to join is first to leave (First In, First Out).

**Applications of Queues:**

1. **Print Jobs**
   - When many people send documents to print, they enter a queue
   - Documents print in the order they were sent

   ![Print Queue](print_queue.png)

2. **Computer Processing**
   - Tasks wait in a queue to be processed by the CPU
   - First task in line gets processed first

3. **Customer Service**
   - Call centers put callers in a queue
   - Calls are answered in the order received

4. **Data Buffers**
   - Used when data transfer speeds don't match
   - Data waits in a queue until it can be processed

5. **Breadth-First Search**
   - In graph algorithms, queues help explore neighbors before moving deeper

### b) Write short notes on:
### i) B++ definition and trees applications

**B++ Trees Definition:**

B++ trees are a type of balanced tree used in databases and file systems. They are similar to B+ trees with some extra connections.

**Key features:**
- All data is stored in leaf nodes
- Leaf nodes are linked together for easy sequential access
- Internal nodes store keys that guide the search

**Example B++ Tree:**
```
         [15]
       /      \
   [5,10]    [20,25]
  /  |  \    /  |  \
[3][6][12] [17][22][30]
```

**Applications of B++ Trees:**

1. **Databases**
   - Store indices to make searches fast
   - Allow quick range queries (find all between X and Y)

2. **File Systems**
   - Organize files for quick access
   - Example: NTFS uses B++ trees

3. **Dictionary Implementations**
   - Store words in order
   - Find words quickly

4. **Geographic Information Systems**
   - Store map data
   - Find locations efficiently

### ii) Resolutions of collisions

**Collision** happens when two items want the same spot in a hash table. Here are ways to solve this:

**1. Chaining**
- Each spot in the hash table holds a linked list
- When collision happens, add the new item to the list
- Simple but uses extra memory

![Chaining](hash_chaining.png)

**2. Open Addressing**

a) **Linear Probing**
- If spot is taken, try next spot
- Keep trying until empty spot is found
- Simple but causes clustering

```
Original hash: slot 5
If slot 5 is full: try slot 6
If slot 6 is full: try slot 7
And so on...
```

b) **Quadratic Probing**
- If spot is taken, try spots at quadratic distances
- Try hash(x)+1², hash(x)+2², hash(x)+3²...
- Reduces clustering

c) **Double Hashing**
- Use a second hash function to decide how far to jump
- If spot is taken, try hash1(x) + i*hash2(x)
- Better distribution

**3. Robin Hood Hashing**
- Take from rich (items close to their ideal position)
- Give to poor (items far from ideal position)
- Reduces worst-case search time

**4. Cuckoo Hashing**
- Use two hash tables
- Each item can go in one of two places
- If both spots full, kick one out and relocate it

## Question 7
### a) Illustrate Warshall's algorithm and find the shortest path between all pairs in the following graph.

Warshall's algorithm (Floyd-Warshall) finds shortest paths between all pairs of vertices in a graph.

**Simple Steps:**
1. Start with a distance matrix showing direct connections
2. For each vertex (k), check if going through k makes any path shorter
3. If path i→k→j is shorter than current i→j, update the distance

**Example with 4 vertices (A, B, C, D):**

Step 1: Create initial distance matrix
- Use actual edge weights for direct connections
- Use ∞ (infinity) for no direct connection
- Use 0 for distance to self

Initial matrix:
```
    A  B  C  D
A  [0, 5, ∞, 10]
B  [∞, 0, 3, ∞]
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```

Step 2: For each vertex as intermediate point, update distances

For k = A:
```
    A  B  C  D
A  [0, 5, ∞, 10]
B  [∞, 0, 3, ∞]
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```
(No changes because no shorter paths through A)

For k = B:
```
    A  B  C  D
A  [0, 5, 8, 10]  ← A→C updated (A→B→C = 5+3 = 8)
B  [∞, 0, 3, ∞]
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```

For k = C:
```
    A  B  C  D
A  [0, 5, 8, 9]   ← A→D updated (A→C→D = 8+1 = 9)
B  [∞, 0, 3, 4]   ← B→D updated (B→C→D = 3+1 = 4)
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```

For k = D:
```
    A  B  C  D
A  [0, 5, 8, 9]
B  [∞, 0, 3, 4]
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```
(No more changes)

Final shortest path matrix:
```
    A  B  C  D
A  [0, 5, 8, 9]
B  [∞, 0, 3, 4]
C  [∞, ∞, 0, 1]
D  [∞, ∞, ∞, 0]
```

This shows the shortest distance between all pairs of vertices.

### b) Write an algorithm to convert infix to prefix for the expression and convert the following expression: A+B-C*D*E^F/G

**Algorithm to Convert Infix to Prefix:**

1. Reverse the infix expression
2. Swap opening and closing brackets: '(' becomes ')' and vice versa
3. Convert this modified expression to postfix using a stack
4. Reverse the postfix expression to get prefix

**Simple Algorithm:**
```
Function InfixToPrefix(expression):
    // Step 1: Reverse the expression
    reversed = Reverse(expression)
    
    // Step 2: Swap brackets
    For each character in reversed:
        If character is '(' then replace with ')'
        If character is ')' then replace with '('
    
    // Step 3: Convert to postfix
    Initialize empty stack and empty result string
    
    For each character in the modified expression:
        If character is operand (letter/number):
            Add to result
        
        If character is '(':
            Push to stack
        
        If character is ')':
            While top of stack is not '(':
                Pop from stack and add to result
            Pop '(' from stack (and discard)
        
        If character is operator (+, -, *, /, ^):
            While stack not empty AND 
                  top of stack has higher/equal precedence:
                Pop from stack and add to result
            Push current operator to stack
    
    While stack not empty:
        Pop from stack and add to result
    
    // Step 4: Reverse to get prefix
    return Reverse(result)
```

**Converting A+B-C*D*E^F/G:**

Step 1: Reverse the expression
```
G/F^E*D*C-B+A
```

Step 2: Swap brackets (none in this example)

Step 3: Convert to postfix using stack:
```
Scan: G    → result: G
Scan: /    → push to stack: [/]
Scan: F    → result: GF
Scan: ^    → push to stack: [/, ^]
Scan: E    → result: GFE
Scan: *    → ^ has higher precedence, pop: result: GFE^
           → push to stack: [/, *]
Scan: D    → result: GFE^D
Scan: *    → equal precedence, pop: result: GFE^D*
           → push to stack: [/, *]
Scan: C    → result: GFE^D*C
Scan: -    → * has higher precedence, pop: result: GFE^D*C*
           → / has higher precedence, pop: result: GFE^D*C*/
           → push to stack: [-]
Scan: B    → result: GFE^D*C*/B
Scan: +    → - has higher precedence, pop: result: GFE^D*C*/B-
           → push to stack: [+]
Scan: A    → result: GFE^D*C*/B-A
Finish     → pop remaining operators: result: GFE^D*C*/B-A+
```

Step 4: Reverse the postfix to get prefix
```
+A-B/*C*D^EFG
```

Therefore, the prefix form of A+B-C*D*E^F/G is:
```
+A-B/*C*D^EFG
```

## Question 8
### Write short notes on any two of the following:

### a) Hashing methods and collisions

**Hashing Methods:**

Hashing is a way to store and find data quickly. It works by:
1. Taking your data
2. Using a formula (hash function) to create an address
3. Storing data at that address

**Main Hash Functions:**

1. **Division Method**
   - h(k) = k mod m
   - Example: For key 25 and table size 7, h(25) = 25 % 7 = 4
   - Simple but may cause clustering

2. **Multiplication Method**
   - h(k) = floor(m × (k × A mod 1))
   - Where A is constant between 0 and 1 (often A ≈ 0.618)
   - Better distribution than division

3. **Universal Hashing**
   - Uses randomly chosen functions from a set
   - Prevents attackers from causing worst-case behavior

4. **Cryptographic Hashing**
   - MD5, SHA-1, SHA-256
   - Makes it impossible to guess input from output
   - Used for security purposes

**Collisions:**

Collisions happen when two items hash to the same location.

**Ways to Handle Collisions:**

1. **Separate Chaining**
   - Each bucket holds a linked list of all items
   - Simple but uses extra memory
   
   ![Separate Chaining](separate_chaining.png)

2. **Open Addressing**
   - Find another spot in the main table
   - Types:
     - Linear probing: try next slot (h+1, h+2, etc.)
     - Quadratic probing: try h+1², h+2², h+3²
     - Double hashing: use second hash function to determine jump size

3. **Performance Impact:**
   - More collisions = slower lookups
   - Good hash functions distribute items evenly
   - Load factor (items/table size) should be kept low

### b) Asymptotic notations used to calculate the best case and average case

**Asymptotic Notations** help us understand how algorithms perform as input size grows, without worrying about exact times.

**Three Main Notations:**

1. **Big O Notation (O)** - Upper Bound
   - Shows the maximum time an algorithm will take
   - Example: O(n²) means time grows no faster than n²
   - Used most often for worst-case analysis

2. **Omega Notation (Ω)** - Lower Bound
   - Shows the minimum time an algorithm will take
   - Example: Ω(n) means time grows at least as fast as n
   - Used for best-case analysis

3. **Theta Notation (Θ)** - Tight Bound
   - Shows when upper and lower bounds match
   - Example: Θ(n log n) means time grows exactly at n log n rate
   - Used when best, worst, and average cases are the same

**Best Case Analysis:**
- The fastest possible time for an algorithm
- Usually shown with Omega (Ω) notation
- Example: Binary search best case is Ω(1) when the target is at the middle

**Average Case Analysis:**
- The expected time across all possible inputs
- Usually shown with Theta (Θ) notation
- Assumes all inputs are equally likely
- Example: QuickSort average is Θ(n log n)

**Example: Linear Search**
- Best case: Ω(1) - item found at first position
- Average case: Θ(n/2) = Θ(n) - check half the list on average
- Worst case: O(n) - check entire list

**Example: Insertion Sort**
- Best case: Ω(n) - array already sorted
- Average case: Θ(n²) - have to shift elements
- Worst case: O(n²) - reverse sorted array

**Why These Matter:**
- Help choose right algorithm for your needs
- Help predict performance with large data
- Independent of hardware or implementation details

### c) Tree sort

**Tree Sort** is a sorting algorithm that uses a Binary Search Tree (BST) to sort elements.

**How Tree Sort Works:**

1. Create an empty Binary Search Tree
2. Insert all elements into the BST one by one
3. Perform an in-order traversal of the BST to get elements in sorted order

**Simple Example:**
To sort [7, 2, 1, 5, 8, 3]:

Step 1: Create BST by inserting each number
```
First: 7        Then: 7       Then:  7     Final Tree:
                     /              / \          7
                    2              2   8        / \
                                  /            2   8
                                 1            / \
                                             1   5
                                                /
                                               3
```

Step 2: In-order traversal (left-root-right) gives sorted list
```
[1, 2, 3, 5, 7, 8]
```

**Time Complexity:**
- Best & Average case: O(n log n)
  - Building BST: O(n log n)
  - In-order traversal: O(n)
- Worst case: O(n²) when tree becomes skewed (like with already sorted data)

**Advantages:**
- Simple to understand and implement
- Online algorithm (can sort as items arrive)
- Stable sort (equal items keep original order)

**Disadvantages:**
- Extra space for tree nodes
- Slow for nearly sorted data
- Not in-place sorting

**Improvement:**
- Use balanced BST (like AVL or Red-Black tree) to guarantee O(n log n) worst case

### d) Binomial Heap

A **Binomial Heap** is a collection of binomial trees that helps efficiently perform operations like finding minimum, merging heaps, inserting items, and deleting items.

**Key Features:**
1. Made of special trees called binomial trees
2. Each binomial tree B₀, B₁, B₂, B₃... has 2^k nodes
3. Trees are arranged by increasing size
4. No two trees have same size

**What is a Binomial Tree?**
- B₀: Single node
- B₁: Two B₀ trees combined (2 nodes)
- B₂: Two B₁ trees combined (4 nodes)
- B₃: Two B₂ trees combined (8 nodes)

![Binomial Trees](binomial_trees.png)

**Example of Binomial Heap with 13 elements:**
```
It would contain:
- One B₃ tree (8 nodes)
- One B₂ tree (4 nodes)
- One B₀ tree (1 node)
(Total: 8 + 4 + 1 = 13 nodes)
```

**Main Operations:**

1. **Find-Min**: O(log n)
   - Check the root of each tree to find minimum

2. **Union (Merge)**: O(log n)
   - Combine heaps like adding binary numbers
   - Merge trees of same size

3. **Insert**: O(log n)
   - Create new B₀ heap with element
   - Union with original heap

4. **Extract-Min**: O(log n)
   - Find and remove minimum
   - Break that tree into smaller trees
   - Merge back with original heap

**Advantages:**
- Efficient merging of heaps
- Good for applications requiring frequent merges
- Useful in graph algorithms like Dijkstra's and Prim's

**Comparison with Fibonacci Heap:**
- Binomial: Simpler implementation
- Fibonacci: Better amortized performance for some operations

# Algorithm Design (MCA-204) Exam Answers

## Question 1

### a) What is a circular linked list? What are the different operations performed on it, explain with an example.

A circular linked list is a special type of linked list where the last node points back to the first node instead of pointing to NULL. This creates a circle-like structure, hence the name "circular" linked list.

**Structure of a Circular Linked List:**
- Each node contains data and a pointer to the next node
- The last node's pointer points back to the first node
- There is no NULL pointer in a circular linked list

**Operations on Circular Linked Lists:**

1. **Insertion:**
   - **Insertion at the beginning:** To insert a new node at the beginning, we create a new node, make it point to the head node, and update the last node to point to this new node.
   - **Insertion at the end:** Create a new node, make it point to the head node, update the previous last node to point to this new node.
   - **Insertion at a specific position:** Traverse to the desired position, adjust the pointers to insert the new node.

2. **Deletion:**
   - **Deletion at the beginning:** Update the last node to point to the second node, and then remove the first node.
   - **Deletion at the end:** Traverse to the second-last node, make it point to the head node, and delete the last node.
   - **Deletion at a specific position:** Traverse to the node just before the target position, adjust the pointers, and delete the target node.

3. **Traversal:**
   - Start from any node and keep moving to the next node until we reach the starting node again.
   - Unlike regular linked lists, we don't check for NULL to stop traversal.

4. **Searching:**
   - Start from the head node and search for the desired element until we either find it or return to the head node.

**Example:**
Let's say we have a circular linked list with nodes containing data: 10, 20, 30, 40.

```
  +---+    +---+    +---+    +---+
  | 10|--->| 20|--->| 30|--->| 40|
  +---+    +---+    +---+    +---+
    ^                          |
    |                          |
    +--------------------------+
```

**Insertion Example (adding 25 after 20):**
1. Create a new node with data 25
2. Find the node with data 20
3. Make the new node point to the node with data 30
4. Make the node with data 20 point to the new node

After insertion:
```
  +---+    +---+    +---+    +---+    +---+
  | 10|--->| 20|--->| 25|--->| 30|--->| 40|
  +---+    +---+    +---+    +---+    +---+
    ^                                   |
    |                                   |
    +-----------------------------------+
```

**Advantages of Circular Linked Lists:**
- No need to maintain a separate pointer to the last node for insertion at the end
- Can traverse the entire list starting from any node
- Useful in applications where we need to repeatedly go around a list (like round-robin scheduling)

### b) Write and discuss various applications of stack and queue data structure in computer science.

#### Stack Applications

A stack is a linear data structure that follows the LIFO (Last In, First Out) principle. Here are its important applications:

1. **Function Call Management (Call Stack):**
   - When a function is called, its execution context is pushed onto the stack
   - When the function completes, its context is popped off the stack
   - This allows for proper function execution order and returning to the right place after function completion
   - Recursion is implemented using the call stack

2. **Expression Evaluation and Conversion:**
   - Converting infix expressions to postfix or prefix notation
   - Evaluating postfix or prefix expressions
   - Checking for balanced parentheses in expressions
   - Example: To evaluate "2 + (3 * 4)", we use stacks to handle operator precedence

3. **Undo/Redo Operations:**
   - Applications like text editors and graphic design software use stacks to implement undo/redo functionality
   - Each action is pushed onto a stack, and when undoing, it's popped off

4. **Browser History:**
   - The back button in browsers uses a stack to remember previously visited pages
   - Each time you visit a new page, it's pushed onto the stack
   - When you click back, the current page is popped off

5. **Syntax Parsing:**
   - Compilers use stacks for syntax parsing and validation
   - Used to check for balanced brackets, parentheses, and braces in code

6. **Memory Management:**
   - In programming languages, memory for local variables is organized in a stack called the "stack memory"
   - Variables are pushed when created and popped when they go out of scope

#### Queue Applications

A queue is a linear data structure that follows the FIFO (First In, First Out) principle. Here are its important applications:

1. **Process Scheduling in Operating Systems:**
   - Ready queue for processes waiting to be executed
   - I/O queue for processes waiting for I/O operations
   - CPU scheduling algorithms like Round Robin use queues to manage processes

2. **Breadth-First Search (BFS):**
   - In graph algorithms, queues are used to implement BFS
   - Helps in finding the shortest path in unweighted graphs
   - Used in network broadcast algorithms

3. **Printer Spooling:**
   - Print jobs are processed in the order they are received
   - Each print request joins the queue and is processed when it reaches the front

4. **Message Buffers:**
   - In message-oriented middleware, messages between applications are stored in queues
   - Ensures messages are processed in the order they are received

5. **Asynchronous Data Transfer:**
   - Between different components in computer systems
   - Between applications in distributed systems
   - Message queues in event-driven programming

6. **Task Scheduling:**
   - Task schedulers use priority queues to determine the order of task execution
   - Tasks with higher priority are dequeued and executed first

7. **Customer Service Systems:**
   - Call centers and customer service applications use queues to handle customer requests in the order they arrive

8. **Cache Implementation:**
   - Some cache replacement policies like FIFO use queue data structure

9. **Real-time Systems:**
   - Managing events and interrupts based on their arrival time
   - Traffic management systems

Both stacks and queues are fundamental data structures that form the building blocks for more complex data structures and algorithms in computer science. Understanding their applications helps in choosing the right data structure for specific problem-solving scenarios.

## Question 2

### a) Draw binary tree using following preorder and inorder traversing:
Preorder - G H O A C K F P D E R H
Inorder - O B K C F A G P E D H R

To construct a binary tree from preorder and inorder traversals, we follow these steps:

1. The first element in preorder is always the root of the tree (G in this case)
2. Find this root element in the inorder traversal
3. Elements to the left of the root in inorder are in the left subtree
4. Elements to the right of the root in inorder are in the right subtree
5. Recursively apply this process to build the left and right subtrees

Let's construct the tree step by step:

1. Preorder starts with G, so G is the root
2. In inorder, G appears after O B K C F A, so these elements form the left subtree
3. Elements P E D H R form the right subtree

For the left subtree:
- The next element in preorder is H, so H is the root of the left subtree
- In inorder, H doesn't appear in the left subtree portion (O B K C F A)
- This suggests the preorder might have an error or the tree has duplicate values

Let me try to construct based on the given sequences:

Root: G
- Left subtree: O B K C F A
- Right subtree: P E D H R

The next element in preorder is H, which should be the root of G's left subtree.
But H doesn't appear in the left subtree portion of inorder.

Given this inconsistency, the most likely tree structure based on the provided traversals would be:

```
        G
       / \
      H   P
     /     \
    O       E
     \     / \
      B   D   R
       \     /
        K   H
       / \
      C   F
         /
        A
```

Note: This is my best interpretation given the traversals provided, but there may be inconsistencies in the original data.

### b) What are the applications of tree data structure? Explain.

Trees are hierarchical data structures that are widely used in various applications in computer science. Here are the key applications of tree data structures:

#### 1. File Systems
Operating systems use tree structures to organize files and directories. The root directory serves as the tree's root, with subdirectories and files as child nodes. This hierarchical organization makes it easy to locate, retrieve, and manage files.

#### 2. Database Systems
- **B-trees and B+ trees**: Used in database management systems and file systems for efficient storage, retrieval, and maintenance of data. They help optimize disk accesses and maintain sorted data.
- **Decision trees**: Used in data mining for classification and prediction.

#### 3. Compilers
- **Abstract Syntax Trees (AST)**: Represent the structure of program code.
- **Parse Trees**: Used in compilers to analyze the grammatical structure of program code.
- **Expression Trees**: Represent mathematical expressions for evaluation.

#### 4. Network Routing
- **Spanning Trees**: Used in network routing protocols to avoid loops in network topologies.
- **Trie structures**: Used for IP routing to find the longest prefix match.

#### 5. Artificial Intelligence
- **Game Trees**: Represent possible moves in games like chess and tic-tac-toe (Minimax algorithm).
- **Decision Trees**: Used for decision making and classification problems.
- **Hierarchical Clustering**: Groups similar data points into a tree structure.

#### 6. Graphics and Multimedia
- **Scene Graphs**: Represent 3D scenes in graphics applications.
- **Quad-trees and Oct-trees**: Used for spatial partitioning in graphics and game development for collision detection and rendering optimization.
- **BSP Trees**: Used in 3D computer graphics to determine visible surfaces.

#### 7. Search Algorithms
- **Binary Search Trees**: Allow quick lookup, insertion, and deletion of items.
- **AVL Trees** and **Red-Black Trees**: Self-balancing BSTs that maintain O(log n) height.
- **Tries**: Efficient for string searching and auto-completion features.

#### 8. Organizational Structures
- **Organization Charts**: Represent hierarchical structures in companies.
- **Family Trees**: Represent genealogical relationships.

#### 9. XML/HTML DOM
Web browsers use trees to represent the Document Object Model (DOM) for HTML/XML documents, allowing for efficient rendering and manipulation of web pages.

#### 10. Computational Biology
- **Phylogenetic Trees**: Represent evolutionary relationships among biological species.
- **RNA Secondary Structure Prediction**: Uses tree structures to predict folding patterns.

#### 11. Compression Algorithms
- **Huffman Coding Trees**: Used in data compression algorithms to assign variable-length codes to characters.

#### 12. Machine Learning
- **Random Forests**: Ensemble learning methods that use multiple decision trees.
- **Boosting Trees**: Like XGBoost, use trees as base learners.

#### 13. Priority Queues
- **Heap Trees**: Implement priority queues for scheduling processes, handling events, and implementing algorithms like Dijkstra's shortest path.

#### 14. Computer Networks
- **Multicast Trees**: For efficient data distribution in networks.
- **Network Topology Representation**: To visualize and analyze network structures.

Trees are versatile data structures that offer efficient solutions to many computational problems. Their hierarchical nature makes them ideal for representing relationships, optimizing searches, and organizing data in a way that reflects real-world hierarchies.

### c) What is hashing? What are the qualities of a good hash function? Explain any two hash function in detail.

#### What is Hashing?

Hashing is a technique that maps data of arbitrary size to fixed-size values. The function that performs this mapping is called a hash function. Hashing is primarily used for:

1. **Fast data retrieval**: Allows O(1) average-case time complexity for lookups
2. **Data integrity verification**: Can detect if data has been modified
3. **Password storage**: Securely storing passwords by saving only their hash values
4. **Implementing associative arrays/dictionaries**: Key-value pair storage
5. **Caching**: Quick lookup of previously computed results

In a hash table, data is stored in an array-like data structure. The hash function converts a key into an index in this array. This allows for quick insertion, deletion, and retrieval of data.

#### Qualities of a Good Hash Function

1. **Deterministic**: The same input should always produce the same hash value.

2. **Uniform Distribution**: Hash values should be evenly distributed across the hash table to minimize collisions. A collision occurs when two different inputs produce the same hash value.

3. **Efficiency**: The hash function should be computationally efficient and quick to calculate.

4. **Avalanche Effect**: Small changes in the input should result in significant changes in the hash value. This helps in distributing the keys uniformly.

5. **Non-Invertible**: It should be practically impossible to derive the original input from its hash value (one-way function). This is especially important for security applications.

6. **Fixed Output Size**: The hash function should produce a fixed-size output regardless of the input size.

7. **Minimizes Collisions**: While collisions cannot be completely eliminated, a good hash function minimizes their occurrence.

8. **Handles Different Data Types**: Should work well for various types of input data (strings, numbers, objects, etc.).

#### Two Hash Functions in Detail

##### 1. Division Method

The division method is one of the simplest hash functions.

**Formula**: h(k) = k mod m

Where:
- k is the key to be hashed
- m is the size of the hash table (usually a prime number)
- h(k) is the resulting hash value

**Working Process**:
1. Take the key k
2. Divide it by the hash table size m
3. Use the remainder as the hash value

**Example**:
- If we have a hash table of size 11 (a prime number)
- And we want to hash the key 42
- h(42) = 42 mod 11 = 9
- So the key 42 would be stored at index 9 in the hash table

**Advantages**:
- Simple and fast to compute
- Works well when the table size is a prime number not close to a power of 2 or 10

**Disadvantages**:
- Not very effective if there are patterns in the keys
- If keys tend to share common factors with m, collisions will be more frequent
- Not suitable for strings or complex objects without preprocessing

**Applications**:
- Simple hash tables with numeric keys
- When computational efficiency is a priority
- In educational contexts to demonstrate hashing concepts

##### 2. Multiplication Method

The multiplication method uses multiplication and modular arithmetic to generate hash values.

**Formula**: h(k) = ⌊m × (k × A mod 1)⌋

Where:
- k is the key to be hashed
- m is the size of the hash table
- A is a constant value between 0 and 1 (often A = (√5 - 1)/2 ≈ 0.618033988749895, known as the golden ratio)
- (k × A mod 1) gives the fractional part of k × A
- ⌊ ⌋ represents the floor function

**Working Process**:
1. Multiply the key k by the constant A
2. Take the fractional part of the result (k × A mod 1)
3. Multiply by the table size m
4. Take the floor of the result to get an integer index

**Example**:
- If we have a hash table of size 10
- We want to hash the key 123
- Using A = 0.618033988749895
- k × A = 123 × 0.618033988749895 = 76.01818061823609
- k × A mod 1 = 0.01818061823609 (fractional part)
- m × (k × A mod 1) = 10 × 0.01818061823609 = 0.1818061823609
- ⌊m × (k × A mod 1)⌋ = ⌊0.1818061823609⌋ = 0
- So the key 123 would be stored at index 0

**Advantages**:
- Less sensitive to patterns in the input data
- Works well with any table size
- Better distribution of hash values compared to division method

**Disadvantages**:
- Slightly more computationally intensive than the division method
- Selection of an appropriate value for A is crucial for performance
- Still needs additional techniques for non-numeric data

**Applications**:
- General-purpose hash tables
- When input keys may have patterns
- Hash tables where the size changes dynamically

#### Universal Hashing

For more robust applications, universal hashing is often used. It involves selecting a hash function randomly from a family of hash functions at runtime. This randomization helps prevent attackers from constructing inputs that would cause many collisions, which could lead to worst-case performance.

#### Handling Collisions

Even with good hash functions, collisions can occur. Two main strategies for handling collisions are:

1. **Chaining**: Each slot in the hash table points to a linked list of entries that hash to the same value.
2. **Open Addressing**: When a collision occurs, the algorithm searches for another empty slot according to a probing sequence (linear probing, quadratic probing, double hashing).

In conclusion, hashing is a powerful technique for implementing efficient data structures like hash tables. The choice of hash function significantly impacts performance and must be selected based on the specific requirements of the application and the nature of the input data.

## Question 3

### a) Sort the following using quick-sort Algorithm: (5, 8, 9, 2, 10, 1, 45, 32)

Quick-sort is a divide-and-conquer sorting algorithm that works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

Let's sort the given array step by step using the quick-sort algorithm:

**Array to be sorted**: [5, 8, 9, 2, 10, 1, 45, 32]

**First Iteration**:
1. Select the first element as the pivot: 5
2. Partition the array:
   - Elements less than 5: [2, 1]
   - Elements greater than or equal to 5: [8, 9, 10, 45, 32]
3. After partitioning: [2, 1, 5, 8, 9, 10, 45, 32]
4. Now we recursively apply quick-sort to the sub-arrays [2, 1] and [8, 9, 10, 45, 32]

**Sort [2, 1]**:
1. Select pivot: 2
2. Partition: 
   - Elements less than 2: [1]
   - Elements greater than or equal to 2: []
3. After partitioning: [1, 2]
4. Both sub-arrays have 0 or 1 elements, so they are sorted

**Sort [8, 9, 10, 45, 32]**:
1. Select pivot: 8
2. Partition:
   - Elements less than 8: []
   - Elements greater than or equal to 8: [9, 10, 45, 32]
3. After partitioning: [8, 9, 10, 45, 32]
4. Recursively sort [9, 10, 45, 32]

**Sort [9, 10, 45, 32]**:
1. Select pivot: 9
2. Partition:
   - Elements less than 9: []
   - Elements greater than or equal to 9: [10, 45, 32]
3. After partitioning: [9, 10, 45, 32]
4. Recursively sort [10, 45, 32]

**Sort [10, 45, 32]**:
1. Select pivot: 10
2. Partition:
   - Elements less than 10: []
   - Elements greater than or equal to 10: [45, 32]
3. After partitioning: [10, 45, 32]
4. Recursively sort [45, 32]

**Sort [45, 32]**:
1. Select pivot: 45
2. Partition:
   - Elements less than 45: [32]
   - Elements greater than or equal to 45: []
3. After partitioning: [32, 45]
4. Both sub-arrays have 0 or 1 elements, so they are sorted

**Combine all the sorted sub-arrays**:
- Sub-array 1: [1, 2]
- Pivot: 5
- Sub-array 2: [8, 9, 10, 32, 45]

**Final sorted array**: [1, 2, 5, 8, 9, 10, 32, 45]

**Algorithm Explanation:**

Quick-sort follows these key steps:

1. **Choose a pivot**: Select an element from the array. Common strategies include:
   - First element (used in our example)
   - Last element
   - Middle element
   - Random element
   - Median of three (first, middle, last)

2. **Partition**: Rearrange the array so that:
   - All elements less than the pivot come before it
   - All elements greater than the pivot come after it
   - The pivot is in its final sorted position

3. **Recursive sorting**: Recursively apply the above steps to the sub-arrays formed by the partition until each sub-array has 0 or 1 elements.

**Time Complexity**:
- Best and Average case: O(n log n)
- Worst case: O(n²), which occurs when the array is already sorted and we choose the first or last element as the pivot

**Space Complexity**:
- O(log n) for the recursive call stack in the best case
- O(n) in the worst case

**Advantages of Quick-sort**:
- In-place sorting (requires minimal additional memory)
- Efficient for large datasets
- Good cache locality
- Easily parallelizable

**Disadvantages**:
- Unstable sorting algorithm (equal elements may change their relative order)
- Worst-case time complexity is O(n²)
- Recursive, which can lead to stack overflow for very large arrays

Quick-sort is one of the most efficient sorting algorithms and is widely used in practice. The choice of pivot and implementation details can significantly affect its performance.

## Question 4

### a) Solve any problem using backtracking.

#### The N-Queens Problem Using Backtracking

**Problem Statement:**
The N-Queens problem asks us to place N chess queens on an N×N chessboard so that no two queens threaten each other. This means no two queens can share the same row, column, or diagonal.

For this example, I'll solve the 4-Queens problem (placing 4 queens on a 4×4 chessboard).

**Understanding Backtracking:**
Backtracking is an algorithmic technique that builds a solution incrementally, abandoning a partial solution ("backtracking") as soon as it determines that the solution cannot be completed to a valid one.

**Approach for Solving N-Queens:**
1. Start in the leftmost column
2. Try placing a queen in each row of the current column
3. If a queen can be placed safely, mark that position
4. Recursively check if this leads to a solution for the rest of the columns
5. If not, remove the queen (backtrack) and try the next row
6. If all rows are tried and no solution is found, return false to trigger backtracking

**Let's solve the 4-Queens problem step by step:**

First, we'll represent the chessboard as a 4×4 matrix where:
- 0 represents an empty cell
- 1 represents a cell with a queen

**Step 1:** Start with an empty board:
```
0 0 0 0
0 0 0 0
0 0 0 0
0 0 0 0
```

**Step 2:** Place a queen in the first row of the first column:
```
1 0 0 0
0 0 0 0
0 0 0 0
0 0 0 0
```

**Step 3:** Try to place a queen in the second column. The first and second rows are under attack, so try the third row:
```
1 0 0 0
0 0 0 0
0 1 0 0
0 0 0 0
```

**Step 4:** Try to place a queen in the third column. The first, second, and third rows are under attack, so try the fourth row:
```
1 0 0 0
0 0 0 0
0 1 0 0
0 0 1 0
```

**Step 5:** Try to place a queen in the fourth column. All rows are under attack, so no valid placement is possible.

**Step 6:** Backtrack to the third column and remove the queen from the fourth row.

**Step 7:** No other valid positions in the third column, so backtrack to the second column.

**Step 8:** Remove the queen from the third row of the second column and try the fourth row:
```
1 0 0 0
0 0 0 0
0 0 0 0
0 1 0 0
```

**Step 9:** Try to place a queen in the third column. The first and fourth rows are under attack, so try the second row:
```
1 0 0 0
0 0 1 0
0 0 0 0
0 1 0 0
```

**Step 10:** Try to place a queen in the fourth column. Only the third row is available:
```
1 0 0 0
0 0 1 0
0 0 0 1
0 1 0 0
```

**Solution found!** This is a valid placement of 4 queens on a 4×4 chessboard.

**Python Implementation of the N-Queens Solution:**

Here's how we would implement this solution in Python:

```python
def solve_n_queens(n):
    """
    Solve the N-Queens problem and return a solution.
    
    Args:
        n: The size of the board and number of queens
    
    Returns:
        A solution board where 1s represent queens
    """
    # Initialize the board with zeros
    board = [[0 for _ in range(n)] for _ in range(n)]
    
    if not solve_n_queens_util(board, 0, n):
        print("No solution exists")
        return None
    
    return board

def solve_n_queens_util(board, col, n):
    """
    Utility function to solve N-Queens problem recursively.
    
    Args:
        board: The chessboard represented as a matrix
        col: Current column being processed
        n: The size of the board
    
    Returns:
        True if a solution is found, False otherwise
    """
    # Base case: If all queens are placed, return True
    if col >= n:
        return True
    
    # Try placing a queen in each row of the current column
    for row in range(n):
        if is_safe(board, row, col, n):
            # Place the queen
            board[row][col] = 1
            
            # Recursively try to place the rest of the queens
            if solve_n_queens_util(board, col + 1, n):
                return True
            
            # If placing queen at board[row][col] doesn't lead to a solution,
            # backtrack - remove the queen from board[row][col]
            board[row][col] = 0
    
    # If no row works, return False to trigger backtracking
    return False

def is_safe(board, row, col, n):
    """
    Check if it's safe to place a queen at board[row][col].
    
    Args:
        board: The chessboard represented as a matrix
        row: Row to check
        col: Column to check
        n: The size of the board
    
    Returns:
        True if it's safe to place a queen, False otherwise
    """
    # Check the left side of this row
    for i in range(col):
        if board[row][i] == 1:
            return False
    
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False
    
    # Check lower diagonal on left side
    for i, j in zip(range(row, n), range(col, -1, -1)):
        if board[i][j] == 1:
            return False
    
    return True

# Function to print the board
def print_board(board):
    for row in board:
        print(" ".join(str(cell) for cell in row))

# Solve 4-Queens problem
solution = solve_n_queens(4)
if solution:
    print_board(solution)
```

This solution demonstrates the backtracking technique:
1. We try to place queens column by column
2. For each column, we try each row
3. If a placement is unsafe, we immediately reject it
4. If a placement is safe, we recursively try to place queens in subsequent columns
5. If we can't place a queen in a column, we backtrack to the previous column and try a different placement
6. We continue this process until we find a solution or exhaust all possibilities

**Applications of Backtracking:**
1. Puzzles like Sudoku, Crosswords, and N-Queens
2. Graph problems like Hamiltonian Path and Graph Coloring
3. Combinatorial problems like Subset Sum and Knapsack
4. Constraint satisfaction problems
5. Parsing expressions in compilers
6. AI applications like game playing and constraint satisfaction

Backtracking is powerful for problems that require exploring multiple possibilities before finding a solution. The key insight is that it allows us to efficiently prune large portions of the search space as soon as we determine they cannot lead to a valid solution.

### b) What do you understand by NP-hard and NP-complete problems?

#### Understanding Computational Complexity: NP-hard and NP-complete Problems

In computer science, problems are classified based on their computational complexity—how difficult they are to solve as the input size grows. NP-hard and NP-complete are important classifications for particularly challenging problems. Let's break them down in simple terms:

#### Basic Complexity Classes

Before diving into NP-hard and NP-complete, let's understand some fundamental complexity classes:

1. **P (Polynomial Time)**:
   - Problems that can be solved in polynomial time (O(n^k) where n is the input size and k is a constant)
   - Examples: Sorting arrays, finding the shortest path in a graph (Dijkstra's algorithm), searching in binary search trees

2. **NP (Non-deterministic Polynomial Time)**:
   - Problems where a proposed solution can be verified in polynomial time
   - All P problems are in NP (if you can solve it quickly, you can verify it quickly too)
   - Examples: The traveling salesman problem, Boolean satisfiability problem (SAT), graph coloring

#### NP-hard Problems

**Definition**: A problem is NP-hard if every problem in NP can be reduced to it in polynomial time.

In simpler terms:
- NP-hard problems are at least as hard as the hardest problems in NP
- If you could solve an NP-hard problem efficiently (in polynomial time), you could solve all NP problems efficiently
- NP-hard problems might not be in NP themselves (they might be even harder)

**Key characteristics**:
1. They represent some of the most challenging computational problems
2. No polynomial-time algorithms are known for NP-hard problems
3. They often involve optimization or finding the best solution among many possibilities

**Examples of NP-hard problems**:
1. **Traveling Salesman Problem (TSP)**: Finding the shortest possible route that visits each city exactly once and returns to the origin city
2. **Knapsack Problem**: Maximizing the value of items in a knapsack without exceeding its weight capacity
3. **Graph Coloring**: Assigning colors to vertices of a graph such that no two adjacent vertices have the same color
4. **Halting Problem**: Determining whether a given program will finish running or continue indefinitely (this is not in NP, but is NP-hard)

#### NP-complete Problems

**Definition**: A problem is NP-complete if:
1. It is in NP (solutions can be verified in polynomial time)
2. It is NP-hard (all problems in NP can be reduced to it in polynomial time)

In simpler terms:
- NP-complete problems are the hardest problems in
