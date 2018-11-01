---
title: valarray 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
ms.openlocfilehash: abfac363388fc86a8b9c68df149bbe65fdd1d427
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482710"
---
# <a name="valarray-class"></a>valarray 類別

此範本類別描述控制序列的項目型別的物件`Type`，儲存成陣列、 專門設計來執行高速的數學運算，以及針對計算效能最佳化。

## <a name="remarks"></a>備註

此類別是一組值的已排序集合之數學概念表示，而此項目是從零開始循序編號。 此類別會描述為最接近的容器，因為它支援一些 (不過並非全部) 第一級序列容器 (例如 [vector](../standard-library/vector-class.md)) 支援的功能。 它與範本類別向量有兩個重大差異：

- 它會定義的對應項目之間的許多算術運算`valarray<Type>`物件相同的類型和長度，例如*xarr* = cos ( *yarr*) + sin ( *zarr*).

- 它定義了各式各樣有趣的方式，以註標`valarray<Type>`物件，藉由多載[運算子&#91;&#93;](#op_at)。

類別的物件`Type`:

- 具有公用預設建構函式、解構函式、複製建構函式和指派運算子，且這些都具有傳統行為。

- 視需要定義算術運算子和數學函式，這些函式定義為具有傳統行為的浮點類型。

特別是在指派之後，細微的差異可能不存在於複製建構和預設建構之間。 沒有任何類別的物件上作業`Type`可能會擲回例外狀況。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[valarray](#valarray)|建構具有特定大小或具有特定值之項目的 `valarray`，或建構為另一個 `valarray` 的複本或另一個 `valarray` 的子集。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[value_type](#value_type)|代表儲存在 `valarray` 中之項目類型的類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[apply](#apply)|將指定的函式套用至 `valarray` 的每個項目。|
|[cshift](#cshift)|定期依指定的位置數目將 `valarray` 中的所有項目移位。|
|[free](#free)|釋放 `valarray` 所使用的記憶體。|
|[max](#max)|尋找 `valarray` 中的最大項目。|
|[min](#min)|尋找 `valarray` 中的最小項目。|
|[resize](#resize)|將 `valarray` 中的項目數目變更為指定的數目，視需要加入或移除項目。|
|[shift](#shift)|依指定的位置數目將 `valarray` 中的所有項目移位。|
|[size](#size)|尋找 `valarray` 中的項目數目。|
|[sum](#sum)|判斷非零長度的 `valarray` 中所有項目的總和。|
|[swap](#swap)||

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!](#op_not)|可取得 `valarray` 中每個項目邏輯 `NOT` 值的一元運算子。|
|[operator%=](#op_mod_eq)|取得陣列項目除以指定的 `valarray` 或除以此項目類型之值的餘數。|
|[operator&=](#op_amp_eq)|取得陣列中項目的位元 `AND` 與指定的 `valarray` 中對應之項目或項目類型的值。|
|[operator>>=](#op_gt_gt_eq)|依位置的指定數目或依第二個 `valarray` 指定的項目數量，將 `valarray` 運算元的每個項目之位元右移。|
|[operator<<=](#op_lt_lt_eq)|依位置的指定數目或依第二個 `valarray` 指定的項目數量，將 `valarray` 運算元的每個項目之位元左移。|
|[operator*=](#op_star_eq)|將指定之 `valarray` 的項目或此項目類型的值和運算元 `valarray` 相乘。|
|[operator+](#op_add)|對 `valarray` 中每個項目套用加號的一元運算子。|
|[operator+=](#op_add_eq)|將指定之 `valarray` 的項目或此項目類型的值加到運算元 `valarray`。|
|[operator-](#operator-)|對 `valarray` 中每個項目套用減號的一元運算子。|
|[operator-=](#operator-_eq)|將運算元 `valarray` 減去指定之 `valarray` 的項目或此項目類型的值。|
|[operator/=](#op_div_eq)|將運算元 `valarray` 除以指定之 `valarray` 的項目或此項目類型的值。|
|[operator=](#op_eq)|指派項目至 `valarray`，其值直接受到指定或指定為其他 `valarray` 的一部份，或由 `slice_array`、`gslice_array`、`mask_array` 或 `indirect_array` 指定。|
|[operator&#91;&#93;](#op_at)|傳回項目參考或其指定索引處的值或指定的子集。|
|[operator^=](#op_xor_eq)|取得陣列的項目互斥邏輯 OR 運算子 (`XOR`) 與指定的 valarray 或此項目型別的值。|
|[operator&#124;=](#op_or_eq)|取得陣列中項目的位元 `OR` 與指定的 `valarray` 中對應之項目或項目類型的值。|
|[operator~](#op_dtor)|可取得 `valarray` 中每個項目位元 `NOT` 值的一元運算子。|

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

## <a name="apply"></a>  valarray::apply

將指定的函式套用至 valarray 的每個項目。

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>參數

*_Func(Type)*<br/>
要套用至運算元 valarray 每個項目的函式物件。

*_Func(const Type&)*<br/>
要套用至運算元 valarray 每個項目的 const 函式物件。

### <a name="return-value"></a>傳回值

Valarray，其項目為已將 `_Func` 套用至運算元 valarray 的項目。

### <a name="remarks"></a>備註

此成員函式會傳回類別的物件[valarray](../standard-library/valarray-class.md)**\<類型 >**，長度為[大小](#size)，每個項目*我*是`_Func((*this)[I])`。

### <a name="example"></a>範例

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
/* Output:
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
*/
```

## <a name="cshift"></a>  valarray::cshift

依指定的位置數目將 valarray 中的所有項目循環移位。

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>參數

*count*<br/>
項目要向前移位的位置數目。

### <a name="return-value"></a>傳回值

新的 valarray，其中的所有項目已移動*計數*循環向 valarray，相對於其運算元 valarray 中的位置前面的位置。

### <a name="remarks"></a>備註

正值*計數*項目循環左移位*計數*放置。

值的負值*計數*循環右移項目移位*計數*放置。

### <a name="example"></a>範例

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
/* Output:
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
*/
```

## <a name="free"></a>  valarray::free

釋放 valarray 使用的記憶體。

```cpp
void free();
```

### <a name="remarks"></a>備註

這個非標準函式相當於指派空的 valarray。 例如: 

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::max

尋找 valarray 中最大的項目。

```cpp
Type max() const;
```

### <a name="return-value"></a>傳回值

運算元 valarray 中最大的項目值。

### <a name="remarks"></a>備註

成員函式會比較值，藉由套用**運算子\<** 或是**運算子 >** 類別的項目配對之間`Type`，哪個運算子必須提供項目`Type`.

### <a name="example"></a>範例

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
*/
```

## <a name="min"></a>  valarray::min

尋找 valarray 中最小的項目。

```cpp
Type min() const;
```

### <a name="return-value"></a>傳回值

運算元 valarray 中最小的項目值。

### <a name="remarks"></a>備註

成員函式會比較值，藉由套用**運算子\<** 或是**運算子 >** 類別的項目配對之間`Type`，哪個運算子必須提供項目`Type`.

### <a name="example"></a>範例

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*/
```

## <a name="op_not"></a>  valarray::operator!

可取得 valarray 中每個項目邏輯 **NOT** 值的一元運算子。

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>傳回值

布林值的 valarray，內容為運算元 valarray 項目值的否定值。

### <a name="remarks"></a>備註

邏輯作業 **NOT** 會否定項目，因為它會將所有的零轉換為一，並將所有的非零值視為一而將它們轉換為零。 傳回的布林值 valarray 與運算元 valarray 的大小相同。

另外還有位元**未**[valarray:: operator ~](#op_dtor)的否定運算的二進位表示法中的個別位元層級**char**並**int** valarray 的項目。

### <a name="example"></a>範例

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_mod_eq"></a>  valarray::operator%=

取得陣列項目除以指定的 valarray 或除以此項目型別之值的餘數。

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要相除的運算元 valarray 項目相同的項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目為運算元 valarray 項目相除餘數的*右*

### <a name="example"></a>範例

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
*/
```

## <a name="and_eq"></a>  valarray::operator&amp;=

取得陣列中項目的位元 **AND** 與指定的 valarray 中對應之項目或項目型別的值。

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray 的項目型別值相同的合併為運算元 valarray 項目，透過邏輯`AND`與運算元 valarray。

### <a name="return-value"></a>傳回值

Valarray，其項目是項目邏輯`AND`藉由為運算元 valarray*右*

### <a name="remarks"></a>備註

僅可用於位元運算操作中的位元**char**並**int**的資料型別及變體而不是在**float**， **double**， **longdouble**， **void**， **bool**，或其他更複雜的資料型別。

位元 AND 有相同的真值表，與邏輯`AND`，但適用於個別位元層級上的資料類型。 假設位元*b*1 和*b*2 *b*1 `AND` *b*2 是**true**如果兩個位元都是 true，**false**如果至少一個為 false。

### <a name="example"></a>範例

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
*/
```

## <a name="op_gt_gt_eq"></a>  valarray::operator&gt;&gt;=

依指定的位置數目或依第二個 valarray 指定的項目數量，將運算元 valarray 的每個項目之位元右移。

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
指出右移數量的值，或是其項目指出項目右移數量的 valarray。

### <a name="return-value"></a>傳回值

Valarray，其項目已經右移指定的數量*右*。

### <a name="remarks"></a>備註

帶正負號的數字會保留其符號。

### <a name="example"></a>範例

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*/
```

## <a name="op_lt_lt_eq"></a>  valarray::operator&lt;&lt;=

依指定的位置數目或依第二個 valarray 指定的項目數量，將運算元 valarray 的每個項目之位元左移。

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
指出左移數量的值，或是其項目指出項目左移數量的 valarray。

### <a name="return-value"></a>傳回值

Valarray，其項目已經左移保留指定的數量*右*。

### <a name="remarks"></a>備註

帶正負號的數字會保留其符號。

### <a name="example"></a>範例

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift"
        << endl << "on the operand array is the valarray:"
        << endl << "( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
on the operand array is the valarray:
( 1 -2 4 -8 16 -32 64 -128 ).
*/
```

## <a name="op_star_eq"></a>  valarray::operator*=

將指定之 valarray 的項目或項目型別的值和運算元 valarray 項目相乘。

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要相乘的運算元 valarray 項目相同的項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目為運算元 valarray 的項目乘積和*右*。

### <a name="example"></a>範例

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="op_add"></a>  valarray::operator+

對 valarray 中每個項目套用加號的一元運算子。

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>傳回值

Valarray，其項目為套用加號的運算元陣列。

### <a name="example"></a>範例

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
*/
```

## <a name="op_add_eq"></a>  valarray::operator+=

將指定之 valarray 的項目或此項目型別的值和運算元 valarray 項目相加。

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要相加的運算元 valarray 項目相同的項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目為運算元 valarray 的項目總和和*右*。

### <a name="example"></a>範例

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
*/
```

## <a name="valarray__operator-"></a>  valarray::operator-

對 valarray 中每個項目套用減號的一元運算子。

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>傳回值

Valarray，其項目為套用減號的運算元陣列。

### <a name="example"></a>範例

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
*/
```

## <a name="valarray__operator-_eq"></a>  valarray::operator-=

從運算元 valarray 減去指定之 valarray 的項目或此項目型別的值。

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要從中減去的運算元 valarray 項目相同的項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目為運算元 valarray 項目的差及*右*。

### <a name="example"></a>範例

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*/
```

## <a name="op_div_eq"></a>  valarray::operator/=

將運算元 valarray 項目除以指定 valarray 的項目或項目型別的值。

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要除的運算元 valarray 項目相同的項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目為運算元 valarray 的項目商數除以*右*。

### <a name="example"></a>範例

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*/
```

## <a name="op_eq"></a>  valarray::operator=

將項目指派給 valarray，其值為直接指定，或是做為某些其他 valarray 的一部分，或是以 slice_array、gslice_array、mask_array 或 indirect_array 指定。

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>參數

*right*<br/>
要複製到運算元 valarray 的 valarray。

*val*<br/>
要指派給運算元 valarray 項目的值。

*_Slicearray*<br/>
要複製到運算元 valarray 的 slice_array。

*_Gslicearray*<br/>
要複製到運算元 valarray 的 gslice_array。

*_Maskarray*<br/>
要複製到運算元 valarray 的 mask_array。

*_Indarray*<br/>
要複製到運算元 valarray 的 indirect_array。

### <a name="return-value"></a>傳回值

第一個成員運算子會以一份所控制的序列取代受控制的序列*右*。

第二個成員運算子與第一個相同，但是具有[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

第三個成員運算子的複本來取代受控制序列的每個項目*val*。

其餘成員運算子會取代其引數所選取之控制序列項目，該引數僅會透過 [operator&#91;&#93;](#op_at) 產生。

如果在取代控制序列中的成員值取決於初始控制序列中的成員，則結果為未定義。

### <a name="remarks"></a>備註

如果控制序列的長度變更，結果通常會是未定義。 不過，在此實作中，此效果只會讓任何針對控制序列中項目的指標或參考失效。

### <a name="example"></a>範例

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
/* Output:
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10
*/
```

## <a name="op_at"></a>  valarray::operator[]

傳回項目參考或其指定索引處的值或指定的子集。

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

valarray<Type> operator[](slice _Slice) const;

valarray<Type> operator[](const gslice& _Gslicearray) const;

valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>參數

*_Off*<br/>
要指派值的項目索引。

*_Slicearray*<br/>
Valarray 的 slice_array，指定要選取或傳回至新 valarray 的子集。

*_Gslicearray*<br/>
Valarray 的 gslice_array，指定要選取或傳回至新 valarray 的子集。

*_Boolarray*<br/>
Valarray 的 bool_array，指定要選取或傳回至新 valarray 的子集。

*_Indarray*<br/>
Valarray 的 indirect_array，指定要選取或傳回至新 valarray 的子集。

### <a name="return-value"></a>傳回值

項目參考或其指定索引處的值或指定的子集。

### <a name="remarks"></a>備註

此成員運算子會多載，以提供數種方式選取的項目從控制的序列<strong>\*這</strong>。 由五個成員運算子構成的第一個群組搭配 [operator=](#op_eq) (和其他指派運算子) 的各種多載，以允許選擇性取代 (切割) 控制序列。 選取的項目必須存在。

當使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 編譯之後，如果您嘗試存取的項目超出 valarray 界限，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

如需如何宣告和使用運算子的範例，請參閱 [slice::slice](../standard-library/slice-class.md#slice) 和 [gslice::gslice](../standard-library/gslice-class.md#gslice) 範例。

## <a name="op_xor_eq"></a>  valarray::operator^=

取得陣列的項目互斥邏輯 OR 運算子 (**XOR**) 與指定的 valarray 或此項目型別的值。

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要透過互斥邏輯 **XOR** 與運算元 valarray 項目合併的相同項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目是項目的互斥邏輯**XOR**運算元 valarray 並*右*。

### <a name="remarks"></a>備註

互斥邏輯 (或稱為 **XOR**) 具有下列語意：假設項目 *e*1 和 *e*2，如果其中只有一個項目為 true，則 *e*1 **XOR** *e*2 為 **true**；如果這兩個項目均為 false 或 true，則為 **false**。

### <a name="example"></a>範例

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<int> vaL ( 10 ), vaR ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL [ i ] =  1;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL [ i ] =  0;
    for ( i = 0 ; i < 10 ; i += 3 )
        vaR [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;
    for ( i = 2 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;

    cout << "The initial operand valarray is:  ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;

    cout << "The  right valarray is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaR [ i ] << " ";
    cout << ")." << endl;

    vaL ^= vaR;
    cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the"
        << endl << "valarray: ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;
}
/* Output:
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*/
```

## <a name="op_or_eq"></a>  valarray::operator&#124;=

取得陣列中項目的位元 `OR` 與指定的 valarray 中對應之項目或項目型別的值。

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>參數

*right*<br/>
Valarray，或是與要透過 `OR` 與運算元 valarray 項目合併的相同項目型別值。

### <a name="return-value"></a>傳回值

Valarray，其項目是項目位元`OR`藉由為運算元 valarray*右*。

### <a name="remarks"></a>備註

僅可用於位元運算操作中的位元**char**並**int**的資料型別及變體而不是在**float**， **double**， **longdouble**， **void**， **bool**，或其他更複雜的資料型別。

位元 `OR` 與邏輯 `OR` 有相同的真值表，但是適用於個別位元層級上的資料型別。 假設位元 *b*1 和 *b*2，如果至少有一個位元為 true，則 *b*1 `OR` *b*2 為 **true**；如果兩個位元均為 false，則為 **false**。

### <a name="example"></a>範例

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial operand valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR"
        << endl << "operator|= is the valarray:"
        << endl << "( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is:
( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
operator|= is the valarray:
( 1 0 1 3 3 4 7 6 7 9 ).
*/
```

## <a name="op_dtor"></a>  valarray::operator~

取得位元的一元運算子`NOT`valarray 中每個項目的值。

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>傳回值

位元的布林值的 valarray，內容`NOT`為運算元 valarray 的項目值。

### <a name="remarks"></a>備註

僅可用於位元運算操作中的位元**char**並**int**的資料型別及變體而不是在**float**， **double**， **longdouble**， **void**， **bool**或其他更複雜的資料型別。

位元 `NOT` 與邏輯 `NOT` 有相同的真值表，但是適用於個別位元層級上的資料型別。 假設位元 *b*，如果 *b* 為 false，則 ~ *b* 為 true，且如果 *b* 為 true，則為 false。 邏輯 **NOT**[operator!](#op_not) 適用於項目層級，會將所有非零的值視為 **true**，且結果為布林值的 valarray。 位元`NOToperator~`，相較之下，可能會導致 valarray 的值非 0 即 1，取決於位元運算的結果。

### <a name="example"></a>範例

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<unsigned short int> vaL1 ( 10 );
    valarray<unsigned short int> vaNOT1 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  5*i;

    cout << "The initial valarray <unsigned short int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL1 [ i ] << " ";
    cout << ")." << endl;

    vaNOT1 = ~vaL1;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT1 [ i ] << " ";
    cout << ")." << endl << endl;

    valarray<int> vaL2 ( 10 );
    valarray<int> vaNOT2 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  -2 * i;

    cout << "The initial valarray <int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL2 [ i ] << " ";
    cout << ")." << endl;

    vaNOT2 = ~vaL2;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;

    // The negative numbers are represented using
    // the two's complement approach, so adding one
    // to the flipped bits returns the negative elements
    vaNOT2 = vaNOT2 + 1;
    cout << "The element-by-element result of "
        << "adding one"
        << endl << "is the negative of the "
        << "original elements the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;
}

/* Output:
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
is the negative of the original elements the
valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
*/
```

## <a name="resize"></a>  valarray::resize

將 valarray 中的項目數變更為指定的數字。

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>參數

*_Newsize*<br/>
重新調整大小的 valarray 中的項目數。

*val*<br/>
要指定給重新調整大小的 valarray 項目的值。

### <a name="remarks"></a>備註

第一個成員函式會使用其預設建構函式來初始化項目。

控制序列中項目的任何指標或參考都會失效。

### <a name="example"></a>範例

下列範例示範 valarray::resize 成員函式的使用。

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a>  valarray::shift

依指定的位置數目將 valarray 中的所有項目移位。

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>參數

*count*<br/>
項目要向前移位的位置數目。

### <a name="return-value"></a>傳回值

新的 valarray，其中的所有項目已移動*計數*valarray，為運算元 valarray 中的位置而言的前端的位置。

### <a name="remarks"></a>備註

正值*計數*項目左移位*計數*個位置，並用零填滿。

值的負值*計數*移位項目右移*計數*個位置，並用零填滿。

### <a name="example"></a>範例

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
*/
```

## <a name="size"></a>  valarray::size

尋找 valarray 中的項目數目。

```cpp
size_t size() const;
```

### <a name="return-value"></a>傳回值

運算元 valarray 中的項目數目。

### <a name="example"></a>範例

下列範例示範 valarray::size 成員函式的使用。

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n"
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a>  valarray::sum

判斷非零長度的 valarray 中所有項目的總和。

```cpp
Type sum() const;
```

### <a name="return-value"></a>傳回值

運算元 valarray 的項目總和。

### <a name="remarks"></a>備註

如果長度大於一，成員函式將值加入至總和藉由套用`operator+=`類別的項目配對之間`Type`，哪一個運算子，因此，必須提供類型的項目`Type`。

### <a name="example"></a>範例

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    int sumva = 0;

    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i+=1 )
        va [ i ] =  i;

    cout << "The operand valarray va (10) is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    sumva = va.sum ( );
    cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
/* Output:
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
*/
```

## <a name="swap"></a>  valarray::swap

交換兩個 `valarray` 的項目。

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|`valarray`，提供要交換的項目。|

### <a name="remarks"></a>備註

此成員函式會交換之間受控制的序列`*this`並*右*。 它以常數時間如此執行，不擲回例外狀況，並且不會使指定此兩個受控制序列中項目的任何參考、指標或迭代器失效。

## <a name="valarray"></a>  valarray::valarray

建構 valarray，其具有特定大小或具有特定值之項目，或做為另一個 valarray 的複本或另一個 valarray 的子集。

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>參數

*計數*<br/>
要放在 valarray 中的項目數目。

*val*<br/>
用來初始化 valarray 中之項目的值。

*ptr*<br/>
值指標，這些值要用來初始化 valarray 中之項目。

*右邊*<br/>
用來初始化新 valarray 的現有 valarray。

*SliceArray*<br/>
slice_array，其項目值要用來初始化建構中 valarray 的項目。

*GsliceArray*<br/>
gslice_array，其項目值要用來初始化建構中 valarray 的項目。

*MaskArray*<br/>
mask_array，其項目值要用來初始化建構中 valarray 的項目。

*IndArray*<br/>
indirect_array，其項目值要用來初始化建構中 valarray 的項目。

*IList*<br/>
initializer_list，包含欲複製的項目。

### <a name="remarks"></a>備註

第一個 (預設) 建構函式將物件初始化為空陣列。 接下來三個建構函式個別初始化物件的陣列*計數*項目，如下所示：

- 如果是明確 `valarray(size_t Count)`，以預設建構函式初始化每個項目。

- 針對`valarray(const Type& Val, Count)`，以初始化每個項目*Val*。

- 對於 `valarray(const Type* Ptr, Count)`，位於 `I` 的項目使用 `Ptr`[`I`] 進行初始化。

其餘的建構函式個別初始化物件為 valarray\<Type> 物件，而該物件由引數指定的子集所決定。

最後一個建構函式相當於倒數第二個，但是它有[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

### <a name="example"></a>範例

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice =\n"
        << "va[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2) {
        cout << v << " ";
    }
    cout << endl;
}

```

```Output
The operand valarray va is:
( 0 2 2 2 2 2 2 2 2 2 )
The new valarray initialized from the slice is vaSlice =
va[slice( 2, 4, 3)] = ( 0 0 0 )
1 2 3 4
```

## <a name="value_type"></a>  valarray::value_type

代表儲存在 valarray 中之項目型別的型別。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Type`的同義字。

### <a name="example"></a>範例

```cpp
// valarray_value_type.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        va [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        va [ i ] =  -1;

    cout << "The initial operand valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    // value_type declaration and initialization:
    valarray<int>::value_type Right = 10;

    cout << "The decalared value_type Right is: "
            << Right << endl;
    va *= Right;
    cout << "The resulting valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;
}
/* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*/
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
