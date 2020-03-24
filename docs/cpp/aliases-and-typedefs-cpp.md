---
title: 別名和 typedef (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 7a45c4570341aca056b9d4c30ea496317a1ac96f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181560"
---
# <a name="aliases-and-typedefs-c"></a>別名和 typedef (C++)

您可以使用*別名*宣告來宣告名稱，以當做先前宣告之類型的同義字使用。 （這種機制也稱為「非正式」*類型別名*）。 您也可以使用此機制來建立*別名範本*，這對自訂配置器特別有用。

## <a name="syntax"></a>語法

```
using identifier = type;
```

## <a name="remarks"></a>備註

*identifier*<br/>
別名的名稱。

*type*<br/>
您要建立別名的類型識別項。

別名不會引入新的類型，而且無法變更現有類型名稱的意義。

別名的最簡單形式相當於 c + + 03 中的**typedef**機制：

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

這兩個都啟用 "counter" 類型變數的建立。 更有用的是像 `std::ios_base::fmtflags` 的這個類類型名：

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

別名也適用于函式指標，但比對等的 typedef 更容易閱讀：

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

**Typedef**機制的限制是它不會與範本搭配使用。 不過，C++11 的類類型名語法啟用別名樣板的建立：

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>範例

下列範例示範如何搭配使用別名樣板與自訂配置器 (在這個案例中為整數向量類型)。 您可以用**int**的任何型別來建立一個方便的別名，以隱藏主要功能程式碼中的複雜參數清單。 在您的程式碼中使用自訂配置器，可以改善可讀性和減少引入錯字所導致 Bug 的風險。

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedefs

**Typedef**宣告導入了一個名稱，在其範圍內，會變成宣告的*類型*宣告部分所指定之型別的同義字。

您可以使用 typedef 宣告，針對語言已經定義的類型或您已經宣告的類型建構較短或更有意義的名稱。 Typedef 名稱可讓您封裝可能變更的實作詳細資料。

相較于**類別**、**結構** **、等位和** **列舉**宣告， **typedef**宣告不會引進新的類型，而是引進現有類型的新名稱。

使用**typedef**宣告的名稱會佔用與其他識別碼相同的命名空間（語句標籤除外）。 因此，除非是在類別類型宣告中，否則這類名稱不能使用與先前宣告的名稱相同的識別項。 請考慮下列範例：

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

與其他識別碼相關的名稱隱藏規則也會管理使用**typedef**宣告之名稱的可見度。 因此，下列範例在 C++ 中是合法的：

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

將相同名稱的區域範圍識別項宣告為 typedef 時，或者宣告相同範圍或內部範圍之結構或等位的成員時，必須指定類型指定名稱。 例如：

```cpp
typedef char FlagType;
const FlagType x;
```

若要重複使用 `FlagType` 名稱做為識別項、結構成員或等位成員的名稱，必須提供類型：

```cpp
const int FlagType;  // Type specifier required
```

只有下列做法是不夠的：

```cpp
const FlagType;      // Incomplete specification
```

因為 `FlagType` 會被當做類型的一部分，而非將重新宣告的識別項。 這個宣告會被視為不合法的宣告，如同

```cpp
int;  // Illegal declaration
```

您可以使用 typedef 宣告任何類型，包括指標、函式和陣列類型。 您可以在定義結構或等位類型之前宣告結構或等位類型指標的 typedef 名稱，只要定義的可見度和宣告相同即可。

### <a name="examples"></a>範例

**Typedef**宣告的其中一種用法是讓宣告更為一致和精簡。 例如：

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

若要使用**typedef**來指定相同宣告中的基本和衍生類型，您可以用逗號分隔宣告子。 例如：

```cpp
typedef char CHAR, *PSTR;
```

下列範例提供類型 `DRAWF` 給未傳回任何值的函式，並且接受兩個 int 引數：

```cpp
typedef void DRAWF( int, int );
```

在上述**typedef**語句之後，宣告

```cpp
DRAWF box;
```

相當於下列宣告：

```cpp
void box( int, int );
```

**typedef**通常會與**結構**結合，以宣告和命名使用者定義的類型：

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>typedef 的重新宣告

**Typedef**宣告可以用來重新宣告相同的名稱，以參考相同的類型。 例如：

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

程式*進程。CPP*包含兩個標頭檔，兩者都包含名稱 `CHAR`的**typedef**宣告。 只要兩個宣告都參考相同的類型，就可以接受此類重新宣告。

**Typedef**無法重新定義先前宣告為不同類型的名稱。 因此，如果*FILE2。H*包含

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

由於嘗試將名稱 `CHAR` 重新定義為參考不同類型，因此編譯器會發出錯誤。 此項重新定義可延伸到如下的建構：

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>與 C C++中的 typedef

由於在**typedef**宣告中宣告未命名結構的 ANSI C 實務，因此支援使用具有類別類型的**typedef**規範。 例如，許多 C 程式設計人員採用下列作法：

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

這類宣告的優點是可以執行類似以下的宣告：

```cpp
POINT ptOrigin;
```

而非：

```cpp
struct point_t ptOrigin;
```

在C++中， **typedef**名稱和實數類型（以**類別**、**結構** **、等**位和**列舉**關鍵字宣告）之間的差異更為相異。 雖然在**typedef**語句中宣告無編號結構的 C 作法仍然有效，但它不會提供任何標記的優點，如同在 C 中所做的一樣。

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

上述範例會使用未命名的類別**typedef**語法，宣告名為 `POINT` 的類別。 `POINT` 是類別名稱；不過，以此方式產生的名稱會受到下列限制：

- 名稱（同義字）不能出現在**類別**、**結構** **或等**位前置詞之後。

- 不可在類別宣告中使用此名稱做為建構函式或解構函式名稱。

總而言之，此語法不提供任何繼承、建構或解構機制。
