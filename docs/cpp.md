# CPP

<!-- vscode-markdown-toc -->

- [Header Files](#HeaderFiles)
- [`g++` Compilation](#gCompilation)
- [Range-based For Loop (since `C++11`)](#Range-basedForLoopsinceC11)
  - [Syntax](#Syntax)
  - [Temporary Range Expression](#TemporaryRangeExpression)
- [`std::vector`](#std::vector)
- [`std::queue`](#std::queue)
  - [`priority_queue`](#priority_queue)
- [`std::map`](#std::map)
- [`std::tuple`](#std::tuple)
- [Miscellaneous](#Miscellaneous)
  - [Check C++ Standard](#CheckCStandard)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

## <a name='HeaderFiles'></a>Header Files

Header files in cpp store predefined functions. It contains definitions of
functions that you can include or import during a preprocessor directive
`#include`.

This preprocessor directive tells the compiler that the header file needs to be
processed prior to the compilation.

## <a name='gCompilation'></a> `g++` Compilation

- When multiple `.cpp` files are needed, all of them need to be included

```console
$ g++ main.cpp $dir/*.cpp -o a.out
```

## <a name='Range-basedForLoopsinceC11'></a>Range-based For Loop (since `C++11`)

### <a name='Syntax'></a>Syntax

```cpp
attr(optional) for (init-statement(opt.) range-declaration : range-expression)
```

### <a name='TemporaryRangeExpression'></a>Temporary Range Expression

## <a name='std::vector'></a> `std::vector`

```cpp
#include <vector>

std::vector<int> v = {1, 2, 3, 4}
```

## <a name='std::queue'></a> `std::queue`

```cpp
#include <queue>
```

### <a name='priority_queue'></a> `priority_queue`

```cpp
std::priority_queue<int> pq {v.begin(), v.end()}
```

## <a name='std::map'></a> `std::map`

```cpp
#include <map>
#include <iostream>

using namespace std;

int main() {
    map<int, int> counter;
    vector<int> v = {4, 4, 5, 5, 5, 6};

    for (auto it = v.begin(); it != v.end(); it++)
    {
        /*
         * Since counter is int-to-int mapping
         * First encounter with any key has an initialized
         * value of 0
         */
        counter[*it] += 1;
    }

    for (auto it = counter.begin(); it != counter.end(); it++)
    {
        // map.key: ->first
        // map.value: ->second
        cout << it->first << " " << it->second << endl;
    }

    return 0;
}
```

## <a name='std::tuple'></a> `std::tuple`

`#include <tuple>`

## <a name='Miscellaneous'></a>Miscellaneous

### <a name='CheckCStandard'></a>Check C++ Standard

```console
$ g++ -x c++  -E -dM -< /dev/null | grep __cplusplus
```
