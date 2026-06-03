---
notion-id: 292982ca-e761-80ec-b7fa-d6083fcb18d7
---
Perfect — here’s your **amended, complete notes**, now including how **pointers interact with functions** in C (pass-by-value vs pass-by-reference behaviour).

Everything below is formatted and consistent with your previous layout.

---

# 🧮 Array Declaration

### **Array Definition Rules**

- **Fixed size only:**
Array size must be a **compile-time constant**, not determined at run time.
- **Syntax:**
```c
type name[size];

```
- **Examples:**
```c
int a[5];          // valid
#define N 10
int b[N];          // valid
int n = 10;
int c[n];          // invalid (runtime size)

```
- **Initialisation:**
You may assign values at definition time:
```c
int d[3] = {1, 2, 3};
int e[]  = {1, 2, 3};   // compiler infers size = 3

```
- **Partial initialisation:**
Unspecified elements become `0`:
```c
int f[5] = {1, 2};   // {1, 2, 0, 0, 0}

```
- **Invalid forms:**
```c
int g[];        // ❌ size not given or inferable
int h[0];       // ❌ zero-length arrays not allowed

```
- **Dynamic arrays:**
For run-time sizing, use pointers with dynamic allocation:
```c
int *p = malloc(n * sizeof(int));

```

---

🧠 **Key idea:**

In ANSI C, array size and contents must be known at **compile time** — dynamic sizing requires **manual memory management**.

---

# 🧭 Pointers

---

### 🧩 **1. What a pointer is**

- A **pointer** is a variable that stores the **address** of another variable
- It “points to” where a value is stored in memory

Example:

```c
int x = 10;
int *p = &x;   // p holds the address of x

```

---

### 🪶 **2. Declaration**

```c
type *pointer_name;

```

- `type` must match the variable it points to
- Examples:
```c
int *p;       // pointer to int
double *q;    // pointer to double
char *s;      // pointer to char

```

---

### 🧠 **3. The address and dereference operators**

- `&` gives the **address** of a variable
-  **dereferences** a pointer → accesses the value it points to

Example:

```c
int n = 5;
int *p = &n;
printf("%d", *p); // *p gives 5 (value at that address)

```

---

### 🧮 **4. Changing values through pointers**

```c
*p = 20;   // changes n to 20

```

When dereferenced, a pointer behaves like the variable it points to.

---

### 🪜 **5. Pointer assignment and compatibility**

- You can assign one pointer to another if they have the same type:
```c
int *a, *b;
a = b;

```
- `void *` is a **generic pointer** type that can hold any address:
```c
void *vp;
vp = &n;  // valid

```

---

### 🧮 **6. Pointers and arrays**

- The name of an array acts as a pointer to its first element
```c
int arr[3] = {1,2,3};
int *p = arr;     // same as &arr[0]
printf("%d", *(p+1)); // prints 2

```

---

### ⚠️ **7. Common errors**

- **Uninitialised pointers:** using before assigning an address
- **Dangling pointers:** pointing to memory that’s freed or out of scope
- **NULL pointers:** always initialise unused pointers to `NULL`
```c
int *p = NULL;

```
- **Out-of-bounds access:** never dereference beyond valid memory

---

### 🧱 **8. Pointer to pointer**

```c
int x = 5;
int *p = &x;
int **pp = &p;   // pointer to pointer

```

---

### 🧰 **9. Dynamic memory (via pointers)**

```c
int *arr = malloc(5 * sizeof(int));
if (arr != NULL) {
    arr[0] = 10;
    free(arr);   // always free dynamically allocated memory
}

```

---

# 🧭 Pointers and Functions in C

### ⚙️ **10. Function arguments — value vs reference**

In C, **all function arguments are passed by value**.

However, if you pass a **pointer**, the *value being copied* is the **address**, giving the effect of “pass by reference.”

---

### 🔹 **Pass by value**

The function receives a *copy* of the variable — the original stays unchanged.

```c
void change(int n) {
    n = 100;
}

int main() {
    int x = 10;
    change(x);   // passes a copy
    printf("%d", x); // prints 10 (unchanged)
}

```

---

### 🔹 **Pass by reference (via pointer)**

The function receives the *address* of a variable — the original can be changed.

```c
void change(int *n) {
    *n = 100;
}

int main() {
    int x = 10;
    change(&x);   // pass address
    printf("%d", x); // prints 100 (changed)
}

```

🧠 The function parameter `int *n` allows indirect modification using `*n`.

---

### 🔹 **Pointers and arrays in functions**

When you pass an array to a function, it decays to a pointer to its first element.

```c
void print(int *arr, int size) {
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
}

int main() {
    int nums[] = {1,2,3,4};
    print(nums, 4);  // array name acts as pointer
}

```

---

### 🔹 **Pointer to pointer for dynamic memory**

Used when a function must allocate memory and return it.

```c
void allocate(int **p) {
    *p = malloc(sizeof(int));
    **p = 42;
}

int main() {
    int *ptr;
    allocate(&ptr);
    printf("%d", *ptr);
    free(ptr);
}

```

---

### 🧩 **Summary of pointer–function behaviour**

| Passing style | Function parameter | Call syntax | Effect on caller |
| --- | --- | --- | --- |
| Pass by value | `int n` | `f(x)` | original unchanged |
| Pass by reference | `int *p` | `f(&x)` | original can change |
| Array (decays to pointer) | `int *arr` | `f(array, size)` | function can modify array contents |
| Pointer to pointer | `int **p` | `f(&ptr)` | function can modify the pointer itself |

---

### 🏁 **Pointer Summary**

| Concept | Symbol | Meaning |
| --- | --- | --- |
| `*` in declaration | pointer type | e.g. `int *p` |
| `&var` | address of `var` | gives pointer |
| `*ptr` | dereference | access value at address |
| `ptr + n` | pointer arithmetic | moves `n` elements ahead |
| `f(&x)` | pass by reference | allows function to modify `x` |

---

Would you like me to include a **diagram showing how **`**pass by value**`** and **`**pass by reference**`** differ in memory** (stack frames and arrows between variables)? It’s very illustrative.