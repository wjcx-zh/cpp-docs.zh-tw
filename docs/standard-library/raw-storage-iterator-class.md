---
title: raw_storage_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
dev_langs:
- C++
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 848612f59c2d5cc24289b6d8c56b0c9eeaebc961
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712786"
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator 類別

提供的配接器類別，可讓演算法將其結果儲存至未初始化的記憶體。

## <a name="syntax"></a>語法

```cpp
template <class OutputIterator, class Type>
class raw_storage_iterator
```

### <a name="parameters"></a>參數

*OutputIterator*<br/>
指定要儲存之物件的輸出迭代器。

*類型*<br/>
正在配置儲存體的物件類型。

## <a name="remarks"></a>備註

此類別描述輸出迭代器建構類型的物件`Type`它所產生的序列中。 類別的物件`raw_storage_iterator` \< **ForwardIterator**，**型別**> 類別的正向迭代器物件，存取儲存體`ForwardIterator`，指定當您建構物件。 物件類別的第一個`ForwardIterator`，運算式 **&\*第一個**必須指定未建構的儲存體的下一個物件 (類型的`Type`) 中產生的序列。

當有需要分隔記憶體配置和物件建構時，會使用此配接器類別。 `raw_storage_iterator` 可以用來將物件複製到未初始化的儲存體，例如使用`malloc` 函式配置的記憶體。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|藉由指定的基礎輸出迭代器建構原始儲存體迭代器。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[element_type](#element_type)|提供一個類型，其描述要儲存在原始儲存體的項目。|
|[iter_type](#iter_type)|提供一個類型，其描述為原始儲存體迭代器基礎的迭代器。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式\* `ii`  =  `x`。|
|[operator=](#op_eq)|指派運算子，用來實作原始儲存體迭代器運算式\* `i`  =  `x`儲存在記憶體中。|
|[operator++](#op_add_add)|原始儲存體迭代器的前置遞增和後置遞增運算子。|

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="element_type"></a>  raw_storage_iterator::element_type

提供一個類型，其描述要儲存在原始儲存體的項目。

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>備註

型別是 raw_storage_iterator 類別範本參數的同義字`Type`。

## <a name="iter_type"></a>  raw_storage_iterator::iter_type

提供一個類型，其描述為原始儲存體迭代器基礎的迭代器。

```cpp
typedef ForwardIterator iter_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `ForwardIterator`的同義字。

## <a name="op_star"></a>  raw_storage_iterator:: operator\*

取值運算子，用來實作原始儲存體迭代器運算式 \* *ii* = *x*。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

### <a name="return-value"></a>傳回值

原始儲存體迭代器的參考

### <a name="remarks"></a>備註

需求`ForwardIterator`是原始儲存體迭代器必須確信只要求運算式\* *ii* = *t*有效，且本身不涉及**運算子**或`operator=`靠自己。 在此實作中的成員運算子會傳回**\*這**，以便[運算子 =](#op_eq)(**constType**&) 可以在運算式中，執行實際的存放區這類\* *ptr* = `val`。

### <a name="example"></a>範例

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
/* Output:
Not constructed.
Copying 5
Constructing 5
*/
```

## <a name="op_eq"></a>  raw_storage_iterator::operator=

指派運算子，用來實作原始儲存體迭代器運算式 \* *i* = *x* 以儲存於記憶體中。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

### <a name="parameters"></a>參數

*val*<br/>
型別的物件的值`Type`要插入到記憶體。

### <a name="return-value"></a>傳回值

運算子會將 `val` 插入記憶體，然後傳回原始儲存體迭代器的參考。

### <a name="remarks"></a>備註

需求`ForwardIterator`狀態，原始儲存體迭代器必須確信只要求運算式\* *ii* = *t*有效，且本身不涉及**運算子**或`operator=`靠自己。 這些成員運算子會傳回 **\*this**。

指派運算子會先使用預存的迭代器值來建構輸出序列中的下一個物件，方法是評估新運算式 **new** ( ( `void` \*)&\* **first**) **Type**( `val`) 的放置。

### <a name="example"></a>範例

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
/* Output:
Not constructed.
Copying 5
Constructing 5
*/
```

## <a name="op_add_add"></a>  raw_storage_iterator::operator++

原始儲存體迭代器的前置遞增和後置遞增運算子。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

### <a name="return-value"></a>傳回值

原始儲存體迭代器或原始儲存體迭代器的參考。

### <a name="remarks"></a>備註

第一個運算子最後會嘗試擷取並儲存型別的物件`CharType`從相關聯的輸入資料流。 第二個運算子會複製物件、遞增物件，然後傳回複本。

第一個前置遞增運算子會遞增預存的輸出迭代器物件，然後傳回 **\*this**。

第二個後置遞增運算子則會複製 **\*this**、遞增預存的輸出迭代器物件，然後傳回複本。

建構函式儲存`first`做為輸出迭代器物件。

### <a name="example"></a>範例

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
/* Output:
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
*/
```

## <a name="raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator

藉由指定的基礎輸出迭代器建構原始儲存體迭代器。

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

### <a name="parameters"></a>參數

*first*<br/>
正向迭代器，是構成要建構之 `raw_storage_iterator` 物件的基礎。

### <a name="example"></a>範例

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
/* Output:
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
*/
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
