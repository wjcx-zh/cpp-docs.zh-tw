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

陣列是一系列相同類型的物件，佔用了連續的記憶體區域。 傳統的 C 樣式陣列是許多 bug 的來源，但仍是常見的，尤其是在較舊的程式碼基底中。 在現代化C++中，我們強烈建議使用[std：： vector](../standard-library/vector-class.md)或[std：： array](../standard-library/array-class-stl.md) ，而不是本節所述的 C 樣式陣列。 這兩個標準程式庫類型會將其元素儲存為連續的記憶體區塊，但提供更大的型別安全，以及保證指向序列內有效位置的反覆運算器。 如需詳細資訊，請參閱[容器C++（現代化）](containers-modern-cpp.md)。

## <a name="stack-declarations"></a>堆疊宣告

在C++陣列宣告中，陣列大小會指定于變數名稱之後，而不是在類型名稱之後，如同其他語言。 下列範例會宣告要在堆疊上配置的1000數列陣列。 元素數目必須以整數常值的形式提供，或做為常數運算式，因為編譯器必須知道要配置多少堆疊空間;它無法使用在執行時間計算的值。 陣列中的每個元素都會被指派預設值0。 如果您未指派預設值，每個元素一開始會包含該位置上的任何隨機值。

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

陣列中的第一個元素是第0個元素，而最後一個元素是（*n*-1）元素，其中*n*是陣列可以包含的元素數目。 宣告中的元素數目必須是整數類資料類型，且必須大於0。 您必須負責確保您的程式永遠不會將值傳遞給大於 `(size - 1)`的注標運算子。

只有當陣列是**結構**或等位中的最後一個欄位，而且已啟用 Microsoft 擴充功能（/ze）**時，大小**為零的陣列才是合法的。

堆疊型陣列的配置和存取速度比堆積型陣列更快，但元素數目不能太大，以致于佔用太多堆疊記憶體。 有多少程度取決於您的程式。 您可以流量分析工具來判斷陣列是否太大。

## <a name="heap-declarations"></a>堆積宣告

如果您需要的陣列太大而無法在堆疊上配置，或其大小在編譯時期無法得知，您可以使用[新的\[\]](new-operator-cpp.md)運算式，在堆積上進行配置。 運算子會傳回第一個元素的指標。 您可以使用注標運算子搭配指標變數，就像使用堆疊型陣列一樣。 您也可以使用[指標算術](../c-language/pointer-arithmetic.md)，將指標移至陣列中的任何任意元素。 您必須負責確保：

- 您一律保留原始指標位址的複本，如此一來，當您不再需要陣列時，就可以刪除記憶體。
- 您不會遞增或遞減超出陣列界限的指標位址。

下列範例顯示如何在執行時間于堆積上定義陣列，以及如何使用注標運算子或使用指標算術來存取陣列元素：

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

您可以在迴圈中初始化陣列，一次一個元素，或在單一語句中初始化。 下列兩個數組的內容相同：

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>將陣列傳遞至函數

將陣列傳遞至函式時，會將它當做第一個元素的指標傳遞。 這適用于堆疊型和以堆積為基礎的陣列。 指標不包含其他大小或類型資訊。 這種行為稱為*指標衰減*。 當您將陣列傳遞至函式時，一定要指定個別參數中的元素數目。 這種行為也意味著陣列元素不會在傳遞至函式時複製。 若要防止函式修改元素，請將參數指定為**const**元素的指標。

下列範例顯示接受陣列和長度的函式。 指標會指向原始陣列，而不是複本。 因為參數不是**const**，所以函式可以修改陣列元素。

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

將陣列宣告為 const，使其成為函式區塊內的唯讀：

```cpp
void process(const double p*, const size_t len);
```

相同的函式也可以使用這些方式來宣告，而不會有任何行為變更。 陣列仍會當做第一個元素的指標傳遞：

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>多維陣列

從其他陣列建構的陣列是多維陣列。 這些多維陣列是藉由依序放置多個包含括號的常數運算式所指定。 例如，以下列宣告為例：

```cpp
int i2[5][7];
```

它會指定**int**類型的陣列，並在概念上以五個數據列的二維矩陣和七個數據行排列，如下圖所示：

![多&#45;維度陣列的概念版面配置](../cpp/media/vc38rc1.gif "多&#45;維度陣列的概念版面配置") <br/>
多維陣列的概念性配置

在具有初始化運算式清單的多維陣列宣告中（如[初始化運算式](../cpp/initializers.md)中所述），可以省略指定第一個維度之界限的常數運算式。 例如：

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

在 n 維陣列型別上使用間接運算子（*）會產生一個 n 維度陣列。 如果 n 是 1，則會產生純量 (或陣列元素)。

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

靜態成員陣列（不論是**const**或 not）是否可以在其定義中初始化（在類別宣告之外）。 例如：

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

## <a name="accessing-array-elements"></a>存取陣列元素

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

在上述程式碼中，`multi` 是**double**類型的三維陣列。 `p2multi` 指標會指向大小為3的**double**類型陣列。 在此範例中，陣列搭配使用的註標有一個、兩個和三個。 雖然更常見的是指定所有註標 (如在 `cout` 陳述式中)，但有時選取陣列元素的特定子集是很有用的 (如 `cout` 之後的陳述式所示)。

## <a name="overloading-subscript-operator"></a>多載注標運算子

就像其他運算子一樣，使用者也可以重新定義注標運算子（`[]`）。 註標運算子的預設行為 (如果未多載) 是使用下列方法結合陣列名稱和註標：

`*((array_name) + (subscript))`

在包含指標類型的所有加法運算中，都會自動執行縮放來調整類型的大小。 因此，結果值不是來自陣列名稱稱來源的*n*個位元組;相反地，它是陣列的第*n*個元素。 如需此轉換的詳細資訊，請參閱[加法類運算子](additive-operators-plus-and.md)。

同樣地，對於多維陣列而言，位址是使用下列方法衍生：

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>運算式中的陣列

當陣列類型的識別碼出現在 `sizeof`、位址（`&`）或參考的初始化以外的運算式中時，它會轉換成第一個陣列元素的指標。 例如：

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指標 `psz` 會指向陣列 `szError1` 的第一個元素。 與指標不同的是，陣列不是可修改的左值。 因此，下列指派是不合法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>另請參閱

[std：： array](../standard-library/array-class-stl.md)
