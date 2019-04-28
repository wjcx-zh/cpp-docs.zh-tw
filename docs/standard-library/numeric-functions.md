---
title: '&lt;numeric&gt; 函式'
ms.date: 11/04/2016
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
ms.openlocfilehash: 6df37cf4f6c8afe09f25550d4fc0d9acb553ac52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236544"
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

*first*<br/>
輸入迭代器，定址對象是要根據指定的二進位運算加總或合併之範圍中的第一個元素。

*last*<br/>
輸入迭代器，定址對象是要根據指定的二進位運算加總或合併之範圍中的最後一個元素，這是在反覆累積中實際包含的最終元素的後面一個位置。

*val*<br/>
每個元素會根據指定的二進位運算，依次與其相加或合併的初始值。

*binary_op*<br/>
要套用至指定範圍內每個元素的二進位運算，以及其先前套用的結果。

### <a name="return-value"></a>傳回值

總和*val*並指定範圍的第一個樣板函式，或為第二個的範本函式，套用指定，而非加總作業，以執行二進位運算的結果中的所有項目 ( *PartialResult， \*Iter*)，其中*PartialResult*是先前的應用程式的作業結果和`Iter`是迭代器，指向範圍中的項目。

### <a name="remarks"></a>備註

初始值可確保會有妥善定義的結果時的範圍是空的在此情況下*val*會傳回。 此二進位運算不一定要是關聯或交替運算。 結果會初始化為初始值*val* ，然後*結果* =  `binary_op` (*結果*， <strong>\*</strong>`Iter`) 透過範圍經過反覆計算其中`Iter`是迭代器，指向範圍內的連續項目。 範圍必須有效，且複雜度與範圍的大小具有線性關係。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

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

*first*<br/>
輸入迭代器，為輸入範圍中的第一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。

*last*<br/>
輸入迭代器，為輸入範圍中的最後一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。

*result*<br/>
輸出迭代器，定址在目的範圍中的第一個項目，該範圍中要存放一系列差異或指定作業的結果。

*binary_op*<br/>
要套用在一般化作業中的二進位運算，取代差異程序的減法運算。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是目的範圍的結尾：`result` + ( `last` - `first`)。

### <a name="remarks"></a>備註

輸出迭代器 _*結果*允許為相同的迭代器做為輸入的迭代器 * 第一，* 以便`adjacent_difference`s 可以就地計算。

值的順序1， 2 3，在輸入範圍中，第一個範本函式會儲存後續`partial_difference`s 12- 1、a3- 2，目的範圍中的。

值的順序1， 2 3，在輸入範圍中，第二個樣板函式會儲存後續`partial_difference`s 1， 2 `binary_op` 1 3 `binary_op` 2，目的範圍中的。

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

*first1*<br/>
輸入迭代器，定址對象是要計算出與第二個範圍之內乘積或一般化內乘積的第一個範圍中的第一個元素。

*last1*<br/>
輸入迭代器，定址對象是要計算出與第二個範圍之內乘積或一般化內乘積的第一個範圍中的最後一個元素。

*first2*<br/>
輸入迭代器，定址對象是要計算出與第一個範圍之內乘積或一般化內乘積的第二個範圍中的第一個元素。

*val*<br/>
範圍之間的內乘積或一般化內乘積要與其相加的初始值。

*binary_op1*<br/>
二進位運算，用來取代套用至內乘積一般化作業中元素乘積的內乘積總和運算。

*binary_op2*<br/>
二進位運算，用來取代內乘積一般化作業中的元素內乘積乘法運算。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回元素乘積的總和，然後為它加上指定的初始值。 因此，針對 *a*i 和 *b*i 值，它會傳回：

`val` + ( *a*1 \* *b*1 ) + ( *a*2 \* *b*2 ) + ... + ( *a*n \* *b*n )

藉由反覆取代*val*具有`val`+ ( 我\* *b*我)。

第二個成員函式會傳回：

`val` *binary_op1* ( 1 *binary_op2* *b*1) *binary_op1* ( 2 *binary_op2* *b*2) *binary_op1* ...*binary_op1* ( n *binary_op2* *b*n)

藉由反覆取代*val*具有`val` *binary_op1* ( 我*binary_op2* *b*i)。

### <a name="remarks"></a>備註

初始值可確保會有妥善定義的結果時的範圍是空的在此情況下*val*會傳回。 這些二進位運算不一定要是關聯或交替運算。 範圍必須有效，且複雜度與範圍的大小具有線性關係。 二元運算子的傳回類型必須可轉換成 **Type**，才能確保可在反覆運算時結束。

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

儲存開始值，從第一個項目，並填入該值的後續增量 (` value++`) 在每個間隔中的項目`[ first,  last)`。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>參數

*first*<br/>
輸入迭代器，定址對象是要填入的範圍中的第一個元素。

*last*<br/>
輸入迭代器，定址對象是要填入的範圍中的最後一個元素。

*value*<br/>
要儲存在第一個元素中並針對後續元素進行後續增量的開始值。

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

*first*<br/>
輸入迭代器，定址範圍中要部分加總或根據指定的二進位運算合併的第一個項目。

*last*<br/>
輸入迭代器，定址範圍中要部分加總或根據指定的二進位運算合併的最後一個項目，這是在反覆累積中實際包含的最終項目之外的一個位置。

*result*<br/>
輸出迭代器，定址在目的範圍中的第一個項目，該範圍中要存放一系列部分總和或指定作業的結果。

*binary_op*<br/>
要套用在一般化作業中的二進位運算，取代部分總和程序的總和運算。

### <a name="return-value"></a>傳回值

輸出迭代器，定址目的範圍結尾： `result` + (`last` - `first`)，

### <a name="remarks"></a>備註

輸出迭代器*結果*允許為相同的迭代器做為輸入的迭代器*第一個*，因此部分總和可以就地計算。

針對輸入範圍中的 *a*1、*a*2、*a*3 值序列，第一個範本函式會將後續部分總和儲存在目的範圍中，其中第 *i* 個元素是由 (  ( ( *a*1 + *a*2) + *a*3) *a*i) 指定。

值序列1， 2 3，在輸入範圍中，第二個範本函式會儲存在目的範圍內，第 i 個項目所在的後續部分總和指定由 ((( 1 `binary_op` 2) `binary_op` 3) 我)。

二進位運算*binary_op*不需要是關聯或交替，因為套用的作業順序已完全指定。

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
