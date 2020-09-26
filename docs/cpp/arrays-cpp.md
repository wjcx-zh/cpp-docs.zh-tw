---
title: 陣列 (C++)
ms.date: 08/03/2020
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 6d002f2baa6657c13ffc603e74828ab60585d3a9
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352787"
---
# <a name="arrays-c"></a>陣列 (C++)

陣列是相同類型的物件序列，其佔用連續的記憶體區域。 傳統的 C 樣式陣列是許多 bug 的來源，但仍然很常見，尤其是在較舊的程式碼基底中。 在新式 c + + 中，我們強烈建議使用 [std：： vector](../standard-library/vector-class.md) 或 [std：： array](../standard-library/array-class-stl.md) ，而不是本節所述的 C 樣式陣列。 這兩個標準程式庫類型都會將其元素儲存為連續的記憶體區塊。 不過，它們提供更高的型別安全，以及保證指向序列內有效位置的支援反覆運算器。 如需詳細資訊，請參閱 [容器](../standard-library/stl-containers.md)。

## <a name="stack-declarations"></a>堆疊宣告

在 c + + 陣列宣告中，陣列大小是指定在變數名稱之後，而不是在類型名稱之後，如同某些其他語言。 下列範例會宣告1000的陣列，這是在堆疊上配置的雙精度浮點數。 元素數目必須以整數常值的形式提供，或做為常數運算式。 這是因為編譯器必須知道要配置多少堆疊空間;它無法使用在執行時間計算的值。 陣列中的每個元素都會被指派預設值0。 如果您沒有指派預設值，每個專案一開始都會包含在該記憶體位置發生的任何隨機值。

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

陣列中的第一個元素是第零個元素。 最後一個元素是 (*n-1*) 元素，其中 *n* 是陣列可包含的元素數目。 宣告中的元素數目必須是整數類資料類型，而且必須大於0。 您必須負責確保程式永遠不會將值傳遞給大於的注標運算子 `(size - 1)` 。

只有當陣列是或中的最後一個欄位 **`struct`** **`union`** ，而且已啟用 Microsoft 擴充功能 (**`/Za`** 或 **`/permissive-`** 未設為) 時，才會有合法的陣列。

以堆疊為基礎的陣列比堆積型陣列更快配置和存取。 不過，堆疊空間有限。 陣列元素的數目不能太大，以致于使用太多的堆疊記憶體。 根據您的程式而定，有多少太多。 您可以使用程式碼剖析工具判斷陣列是否太大。

## <a name="heap-declarations"></a>堆積宣告

您可能需要的陣列太大而無法在堆疊上配置，或其大小在編譯時期不知道。 您可以使用運算式，在堆積上配置此陣列 [`new[]`](new-operator-cpp.md) 。 運算子會傳回第一個元素的指標。 注標運算子在指標變數上的運作方式，與在堆疊型陣列上的運作方式相同。 您也可以使用 [指標算術](../c-language/pointer-arithmetic.md) ，將指標移至陣列中的任何任意元素。 您必須負責確保：

- 您永遠會保留原始指標位址的複本，以便您可以在不再需要陣列時刪除記憶體。
- 您不會遞增或遞減超出陣列界限的指標位址。

下列範例顯示如何在執行時間定義堆積上的陣列。 它會顯示如何使用注標運算子和指標算術來存取陣列元素：

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

您可以在迴圈中初始化陣列、一次一個元素，或在單一語句中初始化。 下列兩個數組的內容相同：

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>將陣列傳遞至函式

當陣列傳遞至函式時，它會以指標的形式傳遞至第一個專案，不論它是堆疊型或堆積型的陣列。 指標不包含其他大小或類型資訊。 這種行為稱為 *指標衰減*。 當您將陣列傳遞至函式時，您必須一律在個別參數中指定專案數。 此行為也表示當陣列傳遞至函數時，不會複製陣列元素。 若要防止函式修改元素，請將參數指定為元素的指標 **`const`** 。

下列範例顯示接受陣列和長度的函式。 指標指向原始陣列，而不是複本。 因為參數不是，所以函式 **`const`** 可以修改陣列元素。

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

將陣列宣告為 const，使其在函式區塊內變成隻讀：

```cpp
void process(const double p*, const size_t len);
```

相同的函式也可以用這些方式宣告，而不會有任何行為變更。 陣列仍會以指標的形式傳遞至第一個元素：

```cpp
// Unsized array
void process(const double p[], const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>多維陣列

從其他陣列建構的陣列是多維陣列。 這些多維陣列是藉由依序放置多個包含括號的常數運算式所指定。 例如，以下列宣告為例：

```cpp
int i2[5][7];
```

它會指定類型的陣列 **`int`** ，並在概念上排列于五個數據列的二維矩陣和七個數據行，如下圖所示：

![多&#45;維度陣列的概念性版面配置](../cpp/media/vc38rc1.gif "多&#45;維度陣列的概念性版面配置") <br/>
多維陣列的概念性配置

您可以宣告具有初始化運算式清單 (的多維陣列，如 [初始化運算式](../cpp/initializers.md)) 中所述。 在這些宣告中，指定第一個維度之界限的常數運算式可以省略。 例如：

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

在 n 維陣列類型上使用間接運算子 ( * ) 會產生 n-1 維度陣列。 如果 n 是 1，則會產生純量 (或陣列元素)。

C++ 陣列是以列為主要順序進行儲存。 以列為主要順序表示最後一個註標變更最快速。

## <a name="example"></a>範例

您也可以在函式宣告中省略多維陣列第一個維度的界限規格，如下所示：

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

撰寫函數 `FindMinToMkt` 是為了讓新的處理站不需要變更任何程式碼，只要重新編譯就可以了。

## <a name="initializing-arrays"></a>初始化陣列

具有類別的函式的物件陣列會由函式初始化。 當初始化運算式清單中的專案數少於陣列中的元素時，預設的函式會用於其餘的元素。 如果未針對類別定義預設的函式，則初始化運算式清單必須 *完整*，也就是陣列中的每個元素都必須有一個初始化運算式。

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

靜態成員陣列 (是否 **`const`** 可以在類別宣告) 以外的 (定義中初始化) 。 例如：

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

使用陣列註標運算子 (`[ ]`)，您可以存取陣列的個別項目。 如果您使用一維陣列的名稱，但沒有注標，則會評估為數組第一個元素的指標。

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

在上述程式碼中， `multi` 是類型的三維陣列 **`double`** 。 `p2multi`指標指向大小為三的陣列類型 **`double`** 。 在此範例中，陣列搭配使用的註標有一個、兩個和三個。 雖然指定所有注標（如同在語句中一樣常見），但 `cout` 有時候選取特定的陣列元素子集會很有用，如下列語句所示 `cout` 。

## <a name="overloading-subscript-operator"></a>多載注標運算子

和其他運算子一樣，可由使用者重新定義 () 的注標運算子 `[]` 。 註標運算子的預設行為 (如果未多載) 是使用下列方法結合陣列名稱和註標：

`*((array_name) + (subscript))`

如同所有包含指標類型的加法，會自動進行調整以調整為類型的大小。 結果值不是來自來源的 *n* 個位元組 `array_name` ，而是陣列的第 *n*個元素。 如需這種轉換的詳細資訊，請參閱 [加法類運算子](additive-operators-plus-and.md)。

同樣地，對於多維陣列而言，位址是使用下列方法衍生：

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>運算式中的陣列

當陣列類型的識別碼出現在以外的運算式中時 **`sizeof`** ，位址 (`&`) 或參考的初始化，會轉換成第一個陣列元素的指標。 例如：

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指標 `psz` 會指向陣列 `szError1` 的第一個元素。 與指標不同的陣列不是可修改的左值。 這就是為什麼下列指派不合法的原因：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>另請參閱

[std：： array](../standard-library/array-class-stl.md)
