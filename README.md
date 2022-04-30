# cpp-style-guide

- [Naming](#naming)
  - [Classes](#classes)
  - [Enum Members](#enum-members)
  - [Functions](#functions)
  - [Global Variables](#global-variables)
  - [Local Variables](#local-variables)
  - [Macros](#macros)
  - [Member Variables](#member-variables)
  - [Namespaces](#namespaces)
  - [Static Variables](#static-variables)

## Naming

- When possible, identifiers should get more specific as they go from left to right
```cpp
// WRONG:
int ageOfCust;
std::string firstNameOfCust;

// RIGHT:                      less specific -> more specific
int custAge;                // cust          -> age
std::string custNameFirst;  // cust          -> name -> first|last

// rule doesn't always make sense to follow:
bool isFirstNameLong, isOptionValueMissing;
```

### Classes

`PascalCase`

```cpp
class CliOption {};

// `Numeric` and `Bool` are adding specificity to `CliOption`
class CliOptionNumeric  : public CliOption {};
class CliOptionBool     : public CliOption {};
```

### Enum Members

`SCREAMING_SNAKE_CASE`
- First member should be explicitly assigned value for clarity

```cpp
enum class Direction {
  NORTH = 0, // assigned explicitly
  EAST,
  SOUTH,
  WEST
};

// also applies to C-style enums (but always prefer enum classes):
typedef enum Dir {
  D_NORTH = 0, // assigned explicitly
  D_EAST,
  D_SOUTH,
  D_WEST
} Dir_t;
```

### Functions

`lower_snake_case`

```cpp
void ant_init();
void ant_move();

// also applies to member functions
class C {
  void do_thing();
};
```

### Global Variables

`g_camelCase`

```cpp
int g_count;
std::string g_str;
```

### Local Variables

`camelCase`

```cpp
void func() {
  int custAge;
  std::string custNameFirst;
}
```

### Macros

`SCREAMING_SNAKE_CASE`

```cpp
#define MACRO 1
#define FUNCTION_LIKE_MACRO(x) (x + 1)
```

### Member Variables

`m_camelCase`

```cpp
class Customer {
  int m_age;
  std::string m_firstName;
};
```

### Namespaces

`flatcase`

- Pick short names (<= 4 chars when possible), abbreviations are ideal

```cpp
namespace lsl   {} // stands for `lslargest`
namespace asc   {} // stands for `ant simulator core`
namespace asl   {} // stands for `ant simulator lite`
namespace cstr  {} // stands for `C string`
```

### Static Variables

`s_camelCase`

```cpp
class C {
  static int s_count;
};

void func() {
  static std::string s_str;
}
```
