---
notion-id: 284982ca-e761-808c-b6f0-ee596c489d7a
---
> [!note]+ # Variable Declarations
> ### ✅ **Rules for valid C variable names**
> 
> 1. Must begin with a **letter (A–Z, a–z)** or an **underscore (**`**_**`**)**.
> 2. Remaining characters may be **letters, digits, or underscores**.
> 3. **No spaces**, **no hyphens**, **no special characters**, and **cannot start with a digit**.
> 4. Avoid names starting with double underscores or `_` followed by uppercase (reserved for compiler).
> 5. A variable declaration specifies a type which can be modified by optional prefixes or qualifiers followed by one or more variable names, ending with a semicolon.
> 6. Variables must be declared before they are used in a block or function.
> 
> Example:
> 
> int x1;
> 
> float y_2, Z3;
> 
> ---
> 
> ## TYPE PREFIX RULES
> 
> C allows certain prefixes before a base type to adjust its meaning or size.
> 
> Prefixes can appear in any order but must make sense for the base type.
> 
> ---
> 
> SIGNED / UNSIGNED
> 
> - Apply only to integer types (char, short, int, long, long long).
> - Define whether the variable can represent negative values.
> - Examples:
> signed int a;
> unsigned long b;
> unsigned char c;
> 
> ---
> 
> SHORT / LONG
> 
> - Apply only to integer types (and to double for “long double”).
> - Indicate the storage size of the integer or precision of the floating type.
> - Examples:
> short int a;
> long int b;
> long long int c;
> long double d;
> 
> ---
> 
> FLOATING-POINT TYPES
> 
> - Only three valid floating types exist:
> float
> double
> long double
> - Prefixes like short, unsigned, or signed are invalid for float or double.
> 
> ---
> 
> CHARACTER TYPES
> 
> - char may be plain, signed, or unsigned:
> char a;
> signed char b;
> unsigned char c;
> 
> ---
> 
> ORDER OF PREFIXES
> 
> - Prefix order does not matter:
> unsigned long int a;
> long unsigned int a;
> 
> ---
> 
> INVALID COMBINATIONS
> 
> - signed float
> - unsigned double
> - short float
> - long float
> - short double
> - unsigned long double
> 
> ---
> 
> SUMMARY
> 
> - signed/unsigned → integers only
> - short/long → integers (plus long double)
> - long double → valid floating type
> - Function definitions cannot be nested, and variables must be declared before use in their scope

> [!note]+ # Constant Declarations
> ## 🔹 **1. General rules**
> 
> - Constants are **fixed values** known at **compile time**.
> - They can be numeric, character, or string.
> - Constants may include **optional prefixes or suffixes** defining **type** and **base**. 
> 
> ---
> 
> ## 🔹 **2. Integer constants**
> 
> **Form:**
> 
> ```plain text
> [base digits][suffix]
> 
> ```
> 
> ### Bases
> 
> - **Decimal:** `0–9` (no leading zero) → `123`
> - **Octal:** starts with `0` → `012`
> - **Hexadecimal:** starts with `0x` or `0X` → `0x1A`
> - **Binary (C23+):** starts with `0b` or `0B` → `0b1010`
> 
> ### Suffixes (optional, case-insensitive, any order)
> 
> - `U` → unsigned
> - `L` → long
> - `LL` → long long
> 
> **Examples:**
> 
> ```plain text
> 100       // int
> 100U      // unsigned int
> 100L      // long int
> 100UL     // unsigned long int
> 0xFFLL    // long long int, hexadecimal
> 
> ```
> 
> ---
> 
> ## 🔹 **3. Floating-point constants**
> 
> **Form:**
> 
> ```plain text
> [digits][.digits][exponent][suffix]
> 
> ```
> 
> ### Components
> 
> - May include a decimal point or an exponent (`E` or `e`).
> - Exponent form: `[digits].[digits]E[+/-]digits`
> - Must have digits before or after the decimal/exponent.
> 
> ### Suffixes
> 
> - `F` or `f` → float
> - `L` or `l` → long double
> - (none) → double
> 
> **Examples:**
> 
> ```plain text
> 3.14       // double
> 3.14F      // float
> 2.0E5L     // long double
> 129.       // valid (double)
> 
> ```
> 
> ---
> 
> ## 🔹 **4. Character constants**
> 
> - Enclosed in **single quotes** `' '`.
> - Represent an **integer value** (the character’s ASCII code).
> - Use **escape sequences** for special characters.
> 
> **Examples:**
> 
> ```plain text
> 'A'     // 65
> '\n'    // newline (10)
> '\x41'  // 'A' in hex
> 
> ```
> 
> ---
> 
> ## 🔹 **5. String constants**
> 
> - Enclosed in **double quotes** `" "`.
> - Stored as an array of `char` ending with a null terminator `'\0'`.
> 
> **Example:**
> 
> ```plain text
> "Hello"  // {'H','e','l','l','o','\0'}
> 
> ```
> 
> ---
> 
> ## 🔹 **6. Symbolic constants**
> 
> - Defined using either `#define` or `const`.
> 
> **Examples:**
> 
> ```plain text
> #define MAX 100
> const int SIZE = 50;
> 
> ```
> 
> ---
> 
> ### ✅ **Summary**
> 
> | Type | Example | Notes |
> | --- | --- | --- |
> | Integer | `42`, `0xFFU`, `075L` | optional base + suffix |
> | Floating | `3.14`, `1E5F`, `2.7L` | decimal or exponent form |
> | Character | `'A'`, `'\n'` | single character (int value) |
> | String | `"Hi"` | null-terminated array |
> | Symbolic | `#define PI 3.14`, `const int N=5;` | named constants |
> 
> ---
> 
> **In short:**
> 
> > C constants are literal values that may include base prefixes, type suffixes, or escape codes.
> > Integers use `U`, `L`, `LL`; floats use `F`, `L`; characters and strings use quotes.
> 
> ### 1. **Integer constants**
> 
> Whole numbers without a fractional part.
> 
> ```c
> 10      // decimal
> 010     // octal (leading 0)
> 0xA     // hexadecimal (leading 0x)
> 
> ```
> 
> You can add **suffixes** to define type and size:
> 
> | Suffix | Meaning |
> | --- | --- |
> | `U` or `u` | unsigned |
> | `L` or `l` | long |
> | `LL` or `ll` | long long |
> 
> Example:
> 
> ```c
> 123U    // unsigned int
> 45L     // long int
> 99ULL   // unsigned long long int
> 
> ```
> 
> ---
> 
> ### 2. **Floating-point constants**
> 
> Numbers with decimal points or exponents.
> 
> ```c
> 3.14
> 2.0e5     // 2 × 10⁵
> 
> ```
> 
> Suffixes specify precision:
> 
> | Suffix | Type |
> | --- | --- |
> | none | double |
> | `F` or `f` | float |
> | `L` or `l` | long double |
> 
> Example:
> 
> ```c
> 3.14F    // float
> 1.23L    // long double
> 
> ```
> 
> ---
> 
> ### 3. **Character constants**
> 
> Single characters in single quotes — actually stored as **integers** (ASCII codes).
> 
> ```c
> 'A'    // 65
> '\n'   // newline (10)
> '\t'   // tab (9)
> 
> ```
> 
> They have **type **`**int**`, not `char`.
> 
> You can use escape sequences for special characters (like `\n`, `\\`, `\'`, `\"`, `\0`).
> 
> ---
> 
> ### 4. **String constants**
> 
> A sequence of characters in **double quotes**, automatically null-terminated (`'\0'` at the end).
> 
> ```c
> "Hello"   // actually 6 bytes: 'H', 'e', 'l', 'l', 'o', '\0'
> 
> ```
> 
> Type: `char[]` (array of characters).
> 
> ---
> 
> ### 5. **Symbolic constants**
> 
> Defined using either `#define` (preprocessor macro) or `const` keyword.
> 
> ### Using `#define`
> 
> ```c
> #define PI 3.14159
> #define MAX 100
> 
> ```
> 
> Replaced by the preprocessor before compilation (no type checking).
> 
> ### Using `const`
> 
> ```c
> const int MAX_USERS = 50;
> const double PI = 3.14159;
> 
> ```
> 
> Type-safe and stored as a true variable in memory, but read-only.
> 
> ---
> 
> ## 🔹 Summary Table
> 
> | Kind | Example | Type | Notes |
> | --- | --- | --- | --- |
> | Integer | `42`, `0xFF`, `75UL` | int, long, etc. | No fractional part |
> | Floating-point | `3.14`, `1e-5`, `2.0L` | float, double, long double | Has decimal or exponent |
> | Character | `'A'`, `'\n'` | int | Single character, stored as integer |
> | String | `"Hello"` | char[] | Sequence of chars ending with `'\0'` |
> | Symbolic | `#define MAX 100`, `const int n=5;` | depends | Named constant, cannot change |
> 
> ---
> 
> **In short:**
> 
> > Constants in C are fixed values known at compile time.
> > They can be numeric, character, or string, and may have type suffixes or prefixes that define their size and kind.

# main()

The entry point to the program and often the exit point.

Returns 0 if the program runs with no errors otherwise returns a non-zero value (usually 1).

```c
 int main(int argc, char **argv)
 {
 /* code goes here */
 return 0;
 }
```

> [!note]+ # printf() format strings
> ```c
>  printf("Colour %s, Decimal %d, Float %0.2f, Char %c\n", \
>  "red", 123, 3.14, 'a');
> ```
> 
> ![[week-1-learning-c-01.png]]
> 
> ![[week-1-learning-c-02.png]]
> 
> ### **a. **`**%3.0c**`** → ❌ Invalid**
> 
> - `%c` prints a **character**, and **precision (**`**.0**`**) is not defined** for it.
> - Width (`3`) is fine, but precision is meaningless for a character — invalid.
> 
> ---
> 
> ### **b. **`**% 5.0f**`** → ✅ Valid**
> 
> - `%f` prints a **floating-point** number.
> - Flags and controls used:
>     - Space (` `): adds a leading space for positive numbers.
>     - Width (`5`): reserves at least 5 characters.
>     - Precision (`.0`): zero digits after the decimal.
> ✅ All are valid for `%f`.
> 
> ---
> 
> ### **c. **`**%3c**`** → ✅ Valid**
> 
> - `%c` prints a single **character**.
> - Width (`3`) pads it to 3 characters total.
> ✅ Valid — precision is not used, but width is allowed.
> 
> ---
> 
> ### **d. **`**%3lc**`** → ❌ Invalid**
> 
> - `%c` expects an `**int**` (promoted `char`).
> - The `l` length modifier is only valid for `%lc` when printing a **wide character** (`wint_t`) using `<wchar.h>` and `wprintf`, **not** with `printf`.
> ❌ Invalid in `printf`.
> 
> ---
> 
> ### **e. **`**%#u**`** → ⚠️ Technically valid, but meaningless**
> 
> - `%u` prints **unsigned decimal integers**.
> - The `#` (alternate form) flag affects only `%o`, `%x`, `%X`, `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g`, `%G`.
> - It’s accepted syntactically but ignored — so semantically pointless.
> ⚠️ Valid syntax, meaningless behaviour.
> 
> ---
> 
> ### **f. **`**%4d**`** → ✅ Valid**
> 
> - `%d` prints **signed integers**.
> - Width (`4`) pads output to at least 4 characters.
> ✅ Fully valid and common.
> 
> ---
> 
> ### **g. **`**%#5.0f**`** → ✅ Valid**
> 
> - `%f` for floats, `#` forces a decimal point even if no digits follow.
> - Width (`5`) and precision (`.0`) are fine.
> ✅ All elements valid for `%f`.
> 
> ---
> 
> ### **h. **`**%-4.0d**`** → ✅ Valid**
> 
> - `%d` prints **signed integers**.
> -  flag → left-align output.
> - Width (`4`) and precision (`.0`) both valid.
> ✅ Correct and meaningful.
> 
> ---
> 
> ### **i. **`**%+4d**`** → ✅ Valid**
> 
> - `%d` for signed integer.
> - `+` flag forces display of sign for positive numbers.
> - Width (`4`) okay.
> ✅ Valid and commonly used.
> 
> ---
> 
> ### **j. **`**%4.0d**`** → ✅ Valid**
> 
> - `%d` integer with width (`4`) and precision (`.0`).
> - Precision sets minimum digits; `.0` means don’t show `0` if value is `0`.
> ✅ Valid and defined behaviour.
> 