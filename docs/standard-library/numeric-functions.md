---
title: '&lt;numeric&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: d5504ed83ce41f38dc69f3fb612438800285d905
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862578"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt; 函式

||||
|-|-|-|
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|
|[iota](#iota)|[partial_sum](#partial_sum)|

## <a name="accumulate"></a>  accumulate

藉由計算連續的部分總和來計算指定範圍內所有元素 (包括某個初始值) 的總和，或是計算連續部分結果 (同樣是使用指定的二進位運算而非加總來計算出) 的結果。

```cpp
template <class InputIterator, class Type>
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type val,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

`first` 輸入迭代器定址範圍中的第一個項目加總或根據指定的二進位運算。

`last` 輸入迭代器定址範圍中的最後一個項目加總或根據指定的二進位運算，超過在反覆累積中實際包含的最後一個元素的一個位置。

`val` 起始值的每個項目會加入或根據指定的二進位運算結合。

`binary_op` 要套用至指定的範圍和其先前的應用程式的結果中的每個項目是二進位運算。

### <a name="return-value"></a>傳回值

針對第一個範本函式，會傳回指定範圍內 `val` 與所有元素的總和，或針對第二個範本函式，會傳回將所指定的二進位運算 (而非加總) 套用到 ( *PartialResult, \*Iter*) 的結果，其中 *PartialResult* 是先前套用運算的結果，而 `Iter` 則是指向該範圍中某個元素的迭代器。

### <a name="remarks"></a>備註

初始值可確保當範圍空白時會有一個妥善定義的結果，在此案例中會傳回 `val`。 此二進位運算不一定要是關聯或交替運算。 結果會初始化為初始值 `val`，然後 *result* = `binary_op` ( *result*, **\***`Iter`) 會在整個範圍經過反覆計算，其中 `Iter` 是指向範圍中後續元素的迭代器。 範圍必須有效，且複雜度與範圍的大小具有線性關係。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

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

## <a name="adjacent_difference"></a>  adjacent_difference

計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。

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
```

### <a name="parameters"></a>參數

`first` 輸入迭代器定址其項目要與其各自的前置有差異，或一對值要由另一個輸入範圍中的第一個項目指定的二進位運算作業。

`last` 輸入迭代器定址的最後一個元素，其元素要與其各自的前置有差異，或一對值要由另一個輸入範圍中指定的二進位運算。

`result` 輸出迭代器定址目的範圍，其中儲存一系列差異或指定之作業的結果的第一個項目。

`binary_op` 要套用在一般化作業取代差異程序中的減法運算的二進位運算。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是目的範圍的結尾：`result` + ( `last` - `first`)。

### <a name="remarks"></a>備註

輸出迭代器 _*結果*允許做為輸入的迭代器的同一個迭代器為 * 首先，* 以便`adjacent_difference`s 可以就地計算。

值的序列1， 2， 3，在輸入範圍內，第一個樣板函式會儲存連續**partial_difference**s1， 2- 1、 a3- 2，目的範圍中的。

針對輸入範圍中的 *a*1、*a*2、*a*3 值序列，第二個範本函式會將後續 **partial_difference**s *a*1、*a*2 `binary_op` *a*1、*a*3 `binary_op` *a*2 儲存在目的範圍中。

二進位運算 `binary_op` 不需要是關聯或交替，因為套用的作業順序已完全指定。

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

## <a name="inner_product"></a>  inner_product

計算兩個範圍的元素乘積總和並將它加到指定的初始值，或計算一般化程序的結果，其中總和及乘積二進位運算會由其他指定的二進位運算取代。

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val,
    BinaryOperation1  binary_op1,
    BinaryOperation2  binary_op2);
```

### <a name="parameters"></a>參數

`first1` 輸入迭代器在其內部產品或第二個範圍的一般化的內部產品是要計算的第一個範圍中的第一個項目定址。

`last1` 輸入迭代器在其內部產品或第二個範圍的一般化的內部產品是要計算的第一個範圍中的最後一個項目定址。

`first2` 輸入迭代器在其內部產品或一般化的內部產品的第一個範圍是要計算第二個範圍中的第一個項目定址。

`val` 要內部產品或通用的範圍之間的內部產品是要加入的初始值。

*binary_op1*二進位運算取代總和套用至項目中的內部產品一般化產品的內部產品操作。

*binary_op2*二進位運算取代 inner 產品項目中的作業的多次內部產品的一般化。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回元素乘積的總和，然後為它加上指定的初始值。 因此，針對 *a*i 和 *b*i 值，它會傳回：

`val` + ( *a*1 \* *b*1 ) + ( *a*2 \* *b*2 ) + ... + ( *a*n \* *b*n )

藉由反覆地取代`val`與`val`+ ( 我\* *b*我)。

第二個成員函式會傳回：

`val` *binary_op1* ( 1 *binary_op2* *b*1) *binary_op1* ( 2 *binary_op2* *b*2) *binary_op1* ...*binary_op1* ( n *binary_op2* *b*n)

藉由反覆地取代`val`與`val` *binary_op1* ( 我*binary_op2* *b*我)。

### <a name="remarks"></a>備註

初始值可確保當範圍空白時會有一個妥善定義的結果，在此案例中會傳回 `val`。 這些二進位運算不一定要是關聯或交替運算。 範圍必須有效，且複雜度與範圍的大小具有線性關係。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

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

## <a name="iota"></a>  iota

儲存一個開始值，以第一個元素開始，然後在間隔 `[ first,  last)` 的每一個元素中，以該值的後續增量 ( ` value++`) 填滿。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>參數

`first` 輸入迭代器，定址要填滿範圍中的第一個項目。

`last` 輸入迭代器，定址要填滿範圍中的最後一個項目。

`value` 儲存在第一個項目和連續遞增後續項目的起始的值。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

以下範例示範 `iota` 函式的一些使用方式，方法是填滿一個整數 [list](../standard-library/list.md)，然後以 `list` 填滿一個 [vector](../standard-library/vector.md)，以便使用 [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) 函式。

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

## <a name="partial_sum"></a>  partial_sum

計算在輸入範圍中從第一個元素到第 *i* 個元素的一系列總和，然後將每個這類總和的結果儲存在目的範圍的第 *i* 個元素中，或計算一般化程序的結果，其中總和運算會由另一個指定的二進位運算取代。

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

`first` 輸入迭代器定址的第一個項目範圍中要部分加總或根據指定的二進位運算合併。

`last` 輸入迭代器，定址範圍中的最後一個項目要部分加總或根據指定的二進位運算合併這是在反覆累積中實際包含的最後一個項目之後的一個位置。

`result` 輸出迭代器定址目的範圍，其中儲存一系列部分總和或指定之作業的結果的第一個項目。

`binary_op` 要套用在一般化作業取代部分總和程序中的總和的二進位運算。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是目的範圍的結尾：`result` + ( `last` - `first`)。

### <a name="remarks"></a>備註

允許輸出迭代器 `result` 與輸入迭代器 `first` 相同，因此部分總和可以就地計算。

針對輸入範圍中的 *a*1、*a*2、*a*3 值序列，第一個範本函式會將後續部分總和儲存在目的範圍中，其中第 *i* 個元素是由 (  ( ( *a*1 + *a*2) + *a*3) *a*i) 指定。

值的序列1， 2， 3，在輸入範圍中，第二個樣板函式會儲存在目的範圍，其中是 ith 項目的後續部分總和所指定 ((( 1 `binary_op` 2) `binary_op` 3) 我)。

二進位運算 `binary_op` 不需要是關聯或交替，因為套用的作業順序已完全指定。

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

## <a name="see-also"></a>另請參閱

[\<numeric>](../standard-library/numeric.md)<br/>
