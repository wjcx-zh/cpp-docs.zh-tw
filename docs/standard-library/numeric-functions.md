---
title: '&lt;numeric&gt; 函式'
description: 描述C++標準程式庫中 &lt;數值&gt;標頭所提供的函式範本。
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419781"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt; 函式

## <a name="accumulate"></a>大量

藉由計算連續的部分總和，來計算指定範圍中所有專案的總和，包括一些初始值。 或者，會計算指定二進位運算的後續部分結果的結果。

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

### <a name="return-value"></a>傳回值

*Init*和第一個樣板函式之指定範圍中的所有專案的總和，或針對第二個樣板函式，將二元*binary_op*運算套用至（* PartialResult， *in_iter*）的結果，其中*PartialResult*是作業先前應用程式的結果，而*in_iter*是指向範圍中下一個元素的反覆運算器。

### <a name="remarks"></a>備註

初始值可確保當範圍是空的時，有一個妥善定義的結果，在此情況下會傳回*init* 。 二進位運算不需要是關聯或交換的。 結果會初始化為初始值*init* ，然後*結果* = *binary_op*（*result*， *in_iter*）會透過範圍反復計算，其中*in_iter*是指向範圍中每個後續元素的反覆運算器。 範圍必須是有效的，而複雜度則是具有範圍大小的線性。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

### <a name="example"></a>範例

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

計算輸入範圍中每個專案及其前置項之間的後續差異。 將結果輸出至目的範圍。 或者，會計算一般化程式的結果，其中差異作業會由另一個指定的二進位運算取代。

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入迭代器，為輸入範圍中的第一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。

*上次*\
輸入迭代器，為輸入範圍中的最後一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。

*結果*\
輸出迭代器，定址在目的範圍中的第一個項目，該範圍中要存放一系列差異或指定作業的結果。

*binary_op*\
要套用在一般化作業中的二進位運算，取代差異程式中減法的運算。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍的結尾： `result` + （`last` - `first`）。

### <a name="remarks"></a>備註

輸出反覆運算器*結果*允許與輸入反覆運算器的*第一個*反覆運算器相同，因此可以就地計算 `adjacent_difference` 值。

針對輸入範圍*中的 1*、 *a*2、 *a*3 值序列，第一個樣板函式會將後續的 *`adjacent_difference` 值（1，* *a*2- *a*1，a3- *a*2）儲存在目的範圍中。

針對輸入範圍中的 1、 *a*2、 *a*3 值序列，第二個樣板函式會在目的範圍中儲存連續 `adjacent_difference` 值1、a 2 *binary_op* *1、* 3 *binary_op* *a*2。 *a* *a* *a*

二進位運算*binary_op*不需要是關聯或交換，因為已指定套用的作業順序。

### <a name="example"></a>範例

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

指定初始值，藉由在範圍上使用 `std::plus<>()` 或指定的二元運算子，來計算獨佔前置詞總和運算。 將結果寫入從指定目的地開始的範圍。 *排除前置*詞總和*表示第 n*個輸入專案未包含在第*n*個總和中。 包含執行原則引數的多載會根據指定的原則執行。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍的結尾：*結果*+ （*最後*一個 * - ）* 。

## <a name="gcd"></a>gcd

計算整數 m 和 n 的最大公除數。

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>參數

*m*、 *n*\
整數類資料類型的值。

### <a name="return-value"></a>傳回值

傳回*m*和*n*絕對值的最大公除數，如果*m*和*n*皆為零，則傳回零。 如果*m*或*n*的絕對值無法以 `common_type_t<M,N>`類型的值表示，則結果會是未定義的。

## <a name="inclusive_scan"></a>inclusive_scan

指定初始值，藉由在範圍上使用 `std::plus<>()` 或指定的二元運算子，來計算內含前置詞總和運算。 將結果寫入從指定目的地開始的範圍。 *內含前置*詞總和表示第*n 個*輸入元素包含在第*n*個總和中。 包含執行原則引數的多載會根據指定的原則執行。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍的結尾：*結果*+ （*最後*一個 * - ）* 。

## <a name="inner_product"></a>inner_product

計算兩個範圍的元素乘積總和並將它加到指定的初始值，或計算一般化程序的結果，其中總和及乘積二進位運算會由其他指定的二進位運算取代。

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>參數

*first1*\
輸入迭代器，定址對象是要計算出與第二個範圍之內乘積或一般化內乘積的第一個範圍中的第一個元素。

*last1*\
輸入迭代器，定址對象是要計算出與第二個範圍之內乘積或一般化內乘積的第一個範圍中的最後一個元素。

*first2*\
輸入迭代器，定址對象是要計算出與第一個範圍之內乘積或一般化內乘積的第二個範圍中的第一個元素。

*init*\
範圍之間的內乘積或一般化內乘積要與其相加的初始值。

*binary_op1*\
二進位運算，用來取代套用至內乘積一般化作業中元素乘積的內乘積總和運算。

*binary_op2*\
二進位運算，用來取代內乘積一般化作業中的元素內乘積乘法運算。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回元素乘積的總和，然後為它加上指定的初始值。 因此，針對 *a*i 和 *b*i 值，它會傳回：

*init* + （*a*1 \* *b*1） + （*a*2 \* *b*2） + ... + （*a*n \* *b*n）

藉由反復將*init*取代為*init* + （*a*i \* *b*i）。

第二個成員函式會傳回：

*init* *binary_op1* （*1* *binary_op2* *b*1） *binary_op1* （*a*2 *binary_op2* *b*2） *binary_op1* .。。*binary_op1* （*n* *binary_op2* *b*n）

藉由反復地以*init*取代*init* *binary_op1* （*a*i *binary_op2* *b*i）。

### <a name="remarks"></a>備註

初始值可確保當範圍是空的時，有一個妥善定義的結果。 在此情況下，會傳回*init* 。 二進位運算不需要是關聯或交換的。 範圍必須是有效的，而複雜度則是具有範圍大小的線性。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

### <a name="example"></a>範例

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>iota

儲存起始值，從第一個元素開始，並在間隔 `[first,  last)`的每個元素中填入該值的後續遞增（`value++`）。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>參數

*第一個*\
輸入迭代器，定址對象是要填入的範圍中的第一個元素。

*上次*\
輸入迭代器，定址對象是要填入的範圍中的最後一個元素。

*value*\
要儲存在第一個專案中的起始值，以及後續遞增的元素。

### <a name="example"></a>範例

以下範例示範 `iota` 函式的一些使用方式，方法是填滿一個整數 [list](../standard-library/list.md)，然後以 [ 填滿一個 ](../standard-library/vector.md)vector`list`，以便使用 [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) 函式。

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>lcm

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

在輸入範圍中，計算從第一個專案到第*n*個元素的一系列總和，並將每個這類總和的結果儲存在目的範圍的第*n*個元素中。 或者，會計算一般化程式的結果，其中總和運算會由另一個指定的二進位運算取代。

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*第一個*\
輸入迭代器，定址範圍中要部分加總或根據指定的二進位運算合併的第一個項目。

*上次*\
輸入迭代器，定址範圍中要部分加總或根據指定的二進位運算合併的最後一個項目，這是在反覆累積中實際包含的最終項目之外的一個位置。

*結果*\
輸出反覆運算器，定址目的範圍的第一個專案，用來儲存部分總和的數列，或指定之二進位運算的後續結果。

*binary_op*\
要套用在一般化作業中的二進位運算，取代部分總和程式中總和的運算。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍的結尾：*結果*+ （*最後*一個 * - ）* 。

### <a name="remarks"></a>備註

輸出反覆運算器*結果*允許與輸入反覆運算器的*第一個*反覆運算器相同，因此可以就地計算部分總和。

如果是值的序列 *，則為*1， *a*2，.。。*在輸入*範圍中的 x，第一個樣板函式會將後續的部分總和儲存在目的範圍中。 第*n* *個元素*是由（1 + *a*2 + *a*3 + ... + *a*n）所提供。

在輸入範圍中，第二個樣板函式會將後續的部分結果儲存在目的範圍中，以*取得一系列的值為*1、 *a*2、 *a*3。 第*n*個元素是由（（.。。（（*a*1 *binary_op* *a*2） *binary_op* *3）* *binary_op* ...）*binary_op* *n）* 。

二進位運算*binary_op*不需要是關聯或交換，因為已指定套用的作業順序。

### <a name="example"></a>範例

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>減少

藉由以任意且可能的排列順序計算總和，來減少指定範圍中的所有專案，可能包括某個初始值。 或者，藉由計算指定二進位運算的結果來減少。 包含執行原則引數的多載會根據指定的原則執行。

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

### <a name="return-value"></a>傳回值

套用*binary_op*或 *`std::plus<>()` 至指定*範圍中的所有專案（* PartialResult， *in_iter*）的結果，其中*PartialResult*是先前的作業應用程式的結果，而*in_iter*是指向範圍中某個元素的反覆運算器。 在未指定*init*的多載中，使用的*init*值相當於 `typename iterator_traits<InputIterator>::value_type{}`。

### <a name="remarks"></a>備註

`reduce` 行為不具決定性，除非*binary_op*是關聯和交換的。 如果*binary_op*修改任何專案，或使間隔中的任何反覆運算器 \[*first*， *last*] （含）失效，則行為是未定義的。

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

使用指定的一元運算子來轉換範圍的專案，然後在指定初始值的範圍內，使用 `std::plus<>()` 或指定的二元運算子，來計算獨佔前置詞總和運算。 將結果寫入從指定目的地開始的範圍。 *排除前置*詞總和*表示第 n*個輸入專案未包含在第*n*個總和中。 包含執行原則引數的多載會根據指定的原則執行。 可能會以任意循序執行總和。

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

*unary_op*\
要套用至指定範圍中每個元素的一元運算。

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

使用指定的一元運算子來轉換範圍的專案，然後在指定初始值的範圍內，使用 `std::plus<>()` 或指定的二元運算子，來計算內含前置詞總和運算。 將結果寫入從指定目的地開始的範圍。 *內含前置*詞總和表示第*n 個*輸入元素包含在第*n*個總和中。 包含執行原則引數的多載會根據指定的原則執行。 可能會以任意循序執行總和。

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

*unary_op*\
要套用至指定範圍中每個元素的一元運算。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

## <a name="transform_reduce"></a>transform_reduce

轉換某個範圍的專案，然後套用仿函數，以任意順序縮小已轉換的元素。 實際上，`transform` 後面接著 `reduce`。

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>參數

*exec*\
執行原則。

*第一個*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op*來加總或結合。

*first1*\
輸入反覆運算器，用於定址範圍中的第一個元素，以使用*binary_op1*來加總或結合。

*上次*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*last1*\
輸入反覆運算器，用於定址範圍中的最後一個專案（使用*binary_op1*），這是在反復累積中實際包含的最後一個專案之外的一個位置。

*結果*\
輸出反覆運算器，用於定址目的範圍的第一個專案，其中的總和或指定作業的結果將會儲存在其中。

*init*\
第一個值，每個專案會接著使用*binary_op*來加入或合併。

*binary_op*\
要套用至指定範圍內的每個專案和其先前應用程式結果的二進位運算。

*unary_op*\
要套用至指定範圍中每個元素的一元運算。

### <a name="return-value"></a>傳回值

轉換後的結果會降低。
