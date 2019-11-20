---
title: 陣列 (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188996"
---
# <a name="arrays-c"></a>陣列 (C++)

An array is a sequence of objects of the same type that occupy a contiguous area of memory. Traditional C-style arrays are the source of many bugs, but are still common, especially in older code bases. In modern C++, we strongly recommend using [std::vector](../standard-library/vector-class.md) or [std::array](../standard-library/array-class-stl.md) instead of C-style arrays described in this section. Both of these standard library types store their elements as a contiguous block of memory but provide much greater type safety along with iterators that are guaranteed to point to a valid location within the sequence. For more information, see [Containers (Modern C++)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Stack declarations

In a C++ array declaration, the array size is specified after the variable name, not after the type name as in some other languages. The following example declares an array of 1000 doubles to be allocated on the stack. The number of elements must be supplied as an integer literal or else as a constant expression because the compiler has to know how much stack space to allocate; it cannot use a value computed at run-time. Each element in the array is assigned a default value of 0. If you do not assign a default value, each element will initially contain whatever random values happen to be at that location.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

The first element in the array is the 0th element, and the last element is the (*n*-1) element, where *n* is the number of elements the array can contain. The number of elements in the declaration must be of an integral type and must be greater than 0. It is your responsibility to ensure that your program never passes a value to the subscript operator that is greater than `(size - 1)`.

A zero-sized array is legal only when the array is the last field in a **struct** or **union** and when the Microsoft extensions (/Ze) are enabled.

Stack-based arrays are faster to allocate and access than heap-based arrays, but the number of elements can't be so large that it uses up too much stack memory. How much is too much depends on your program. You can use profiling tools to determine whether an array is too large.

## <a name="heap-declarations"></a>Heap declarations

If you require an array that is too large to be allocated on the stack, or whose size cannot be known at compile time, you can allocate it on the heap with a [new\[\]](new-operator-cpp.md) expression. The operator returns a pointer to the first element. You can use the subscript operator with the pointer variable just as with a stack-based array. You can also use [pointer arithmetic](../c-language/pointer-arithmetic.md) to move the pointer to any arbitrary elements in the array. It is your responsibility to ensure that:

- you always keep a copy of the original pointer address so that you can delete the memory when you no longer need the array.
- you do not increment or decrement the pointer address past the array bounds.

The following example shows how to define an array on the heap at run time, and how to access the array elements using the subscript operator or by using pointer arithmetic:

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>初始化陣列

You can initialize an array in a loop, one element at a time, or in a single statement. The contents of the following two arrays are identical:

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Passing arrays to functions

When an array is passed to a function, it is passed as a pointer to the first element. This is true for both stack-based and heap-based arrays. The pointer contains no additional size or type information. This behavior is called *pointer decay*. When you pass an array to a function, you must always specify the number of elements in a separate parameter. This behavior also implies that the array elements are not copied when the array is passed to a function. To prevent the function from modifying the elements, specify the parameter as a pointer to **const** elements.

The following example shows a function that accepts an array and a length. The pointer points to the original array, not a copy. Because the parameter is not **const**, the function can modify the array elements.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Declare the array as const to make it read-only within the function block:

```cpp
void process(const double p*, const size_t len);
```

The same function can also be declared in these ways, with no change in behavior. The array is still passed as a pointer to the first element:

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Multidimensional arrays

從其他陣列建構的陣列是多維陣列。 這些多維陣列是藉由依序放置多個包含括號的常數運算式所指定。 例如，以下列宣告為例：

```cpp
int i2[5][7];
```

It specifies an array of type **int**, conceptually arranged in a two-dimensional matrix of five rows and seven columns, as shown in the following figure:

![Conceptual layout of a multi&#45;dimensional array](../cpp/media/vc38rc1.gif "Conceptual layout of a multi&#45;dimensional array") <br/>
多維陣列的概念性配置

In declarations of multidimensioned arrays that have an initializer list (as described in [Initializers](../cpp/initializers.md)), the constant expression that specifies the bounds for the first dimension can be omitted. 例如:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

上述宣告會定義一個三列四行的陣列。 資料列代表工廠，資料行則代表工廠出貨的市場。 值是從工廠到市場的運費。 陣列的第一個維度會被省略，但編譯器會藉由檢查初始設定式填入該維度。

Use of the indirection operator (*) on an n-dimensional array type yields an n-1 dimensional array. If n is 1, a scalar (or array element) is yielded.

C++ 陣列是以列為主要順序進行儲存。 以列為主要順序表示最後一個註標變更最快速。

## <a name="example"></a>範例

省略多維陣列中第一個維度之界限規格的技術也可用於函式宣告，如下所示：

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

若撰寫 `FindMinToMkt` 函式，加入新的工廠時就不需要變更任何程式碼，只需要重新編譯。

## <a name="initializing-arrays"></a>初始化陣列

如果類別具有建構函式，該類別的陣列會以建構函式進行初始化。 如果初始設定式清單中的項目少於陣列中的元素數目，則其餘元素會使用預設建構函式。 如果該類別未定義預設建構函式，則初始設定式清單必須完整，也就是說，陣列中的每個元素都必須有一個初始設定式。

以定義兩個建構函式的 `Point` 類別為例：

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

`aPoint` 的第一個元素是使用 `Point( int, int )` 建構函式建構，其餘兩個元素則是使用預設建構函式建構。

Static member arrays (whether **const** or not) can be initialized in their definitions (outside the class declaration). 例如:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Accessing array elements

使用陣列註標運算子 (`[ ]`)，您可以存取陣列的個別項目。 如果一維陣列用於沒有註標的運算式，陣列名稱判斷值為陣列中第一個項目的指標。

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

當您使用多維陣列時，您可以在運算式中使用各種組合。

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

In the preceding code, `multi` is a three-dimensional array of type **double**. The `p2multi` pointer points to an array of type **double** of size three. 在此範例中，陣列搭配使用的註標有一個、兩個和三個。 雖然更常見的是指定所有註標 (如在 `cout` 陳述式中)，但有時選取陣列元素的特定子集是很有用的 (如 `cout` 之後的陳述式所示)。

## <a name="overloading-subscript-operator"></a>Overloading subscript operator

Like other operators, the subscript operator (`[]`) can be redefined by the user. 註標運算子的預設行為 (如果未多載) 是使用下列方法結合陣列名稱和註標：

`*((array_name) + (subscript))`

在包含指標類型的所有加法運算中，都會自動執行縮放來調整類型的大小。 Therefore, the resultant value is not *n* bytes from the origin of array-name; rather, it is the *n*th element of the array. For more information about this conversion, see [Additive operators](additive-operators-plus-and.md).

同樣地，對於多維陣列而言，位址是使用下列方法衍生：

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>運算式中的陣列

當陣列類型的識別項出現在 `sizeof`、傳址 (`&`)，或是參考的初始化中時，會將它轉換成第一個陣列元素的指標。 例如:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指標 `psz` 會指向陣列 `szError1` 的第一個元素。 Arrays, unlike pointers, are not modifiable l-values. 因此，下列指派是不合法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>請參閱

[std::array](../standard-library/array-class-stl.md)
