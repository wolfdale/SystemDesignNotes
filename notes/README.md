# Java Collections & complexities.
Rule of thumb Big-O time complexities. 
Best  ----------------------------------------------------------------- Worst

O(1) -> O(log n) -> O(n) -> O(n log n) -> O(n^2) -> O(2 ^ n) -> O(n!)

**1. Map // collection**  
1. Definition ->Map<K, V> map = new HashMap<>();  
2. Insert / Update -> V put(k1, v1); // TC: O(1)  
3. Delete -> V remove(k1); // TC: O(1)  
4. Get -> V get(k1); // TC: O(1)  
5. Size -> int size(); // TC: O(1)  
6. Check for empty -> boolean isEmpty(); // TC: O(1)  
7. Value present -> boolean containsKey(k1); // TC: O(1)  
8. Remove all map values -> clear(); // TC: O(2n + 1) -> O(n)  _(n-key, n-value, 1 for map itself)_

**2. ArrayList // Collection**  
1. Definition -> ArrayList list = new ArrayList<>();  
2. Insert -> boolean add(t)  **[TC: O(1)]**  / add(int index, T)  **[TC: O(n)]**  
3. Delete -> T remove(int index); // TC: O(n) as you have to shuffle the elements above that point  
4. Set/Update index value -> T set(int index, T); // TC: O(1)  
5. Get index-> T get(int index); // TC: O(1)  
6. Size -> int list.size(); // TC: O(1)  
7. Clear elements -> void clear(); // TC: O(n) & removeAll : O(n^2).  
8. Check for Empty -> boolean isEmpty(); // TC: O(1)  
9. Value contain check -> boolean contains(t); // TC: O(n)  
10. Get Index of value -> int indexOf(t); // TC: O(n), checking each element one by one  
11. Non primitive to primitive list -> toArray(); // TC: O(n)  
12. Sorting for List ->

-   Collections.sort(list, (a, b) -> a - b); // ascending , TC: O(nlogn)
-   Collections.sort(list, (a, b) -> b - a); // descending , TC: O(nlogn)

**3. Array**  
1. Definition ->T arr [ ]= new T[N]; // N: static size , T : datatype  
2. Insert -> arr[index] = v1; // TC: O(1)  
3. Update -> arr[index] = v2; // TC: O(1)  
4. Get -> T arr[index] // TC: O(1)  
5. Size -> int arr.length // TC: O(1)  
6. Arrays.fill(arr, 0); // filled array with value=0, TC: O(n)  
7. Sorting -> TC: O(nlogn)

-   Primitive (int[] ..)
    -   Arrays.sort(arr); // default ascending,
-   Non-primitive (Integer[] ..)
    -   Arrays.sort(arr); // default ascending
    -   Arrays.sort(arr, (a,b) -> b-a); // descending

**4. Stack // Collection**  
1. Definition ->Stack st = new Stack<>();  
2. Insert -> T push(t); // TC: O(1)  
3. Size -> int size(); // TC: O(1)  
4. Look up for head element -> T peek(); // TC: O(1)  
5. Remove head element -> T pop(); // TC: O(1)  
6. Check for Empty -> boolean isEmpty(); // TC: O(1)

**5. Queue // Collection**  
1. Definition -> Queue queue = new LinkedList<>();  
2. Insert -> boolean add(t); // TC: O(1)  
3. Size -> int size(); // TC: O(1)  
4. Look up for head element -> T peek(); // TC: O(1)  
5. Remove head element -> T poll(); // TC: O(1)  
6. Check for Empty -> boolean isEmpty(); // TC: O(1)  
7. Points to remember :

-   Queue poll vs Stack pop
-   Queue add vs Stack push
-   We can define queue via LinkedList, PriorityQueue based on use case

**6. String / StringBuilder**  
1. Definition -> String str = new String();  
2. Size -> int length();// TC: O(1)  
3. Convert to char Array -> toCharArray(); // TC: O(n)  
4. Value for specific index -> charAt(int index); // TC: O(1)  
5. Substring from string -> substring(a,b] // a : inclusive, b: Exclusive, TC: O(n)  
6. Transform to Lowercase -> toLowerCase(); // TC: O(n)  
7. Transform to UpperCase -> toUpperCase(); // TC: O(n)  
8. Replace all characters in string -> replaceAll(from, to) // TC: O(n)  
9. Some useful Character properties

-   Character.isLetter();
-   Character.isAlphabetic();
-   Character.isUpperCase();
-   Character.isLowerCase();
-   Character.isDigit();

10.  Concatenation

-   T str1 + str2
-   StringBuilder ->
    -   new StringBuilder() / new StringBuilder(int)
    -   append("adding string") // better way to do
    -   toString() // converting back to string

**7. HashSet // Collection**  
1. Definition ->Set set = new HashSet<>();  
2. Insert / update -> boolean add(t); // TC: O(1)  
3. Delete -> boolean remove(t); // TC: O(1)  
4. Get -> boolean contains(t); // TC: O(1)  
5. Size -> int size(); // TC: O(1)  
6. Check for Empty -> boolean isEmpty(); // TC: O(1)  
7. Remove all set values -> clear(); // TC: O(n)
