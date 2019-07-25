---
title: slice 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 830e345eb7522cef44dbf6e727a976fb79c1e081
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450350"
---
# <a name="slice-class"></a>slice 類別

valarray 的一個公用程式類別，用來定義父代 valarray 的一維子集。 如果 valarray 被視為含有陣列中所有元素的二維矩陣，則配量會從二維陣列中擷取一維的向量。

## <a name="remarks"></a>備註

此類別會儲存用來描述類型 [slice_array](../standard-library/slice-array-class.md) 之物件特性的參數。當類別 slice 的物件顯示為類別 [valarray](../standard-library/valarray-class.md#op_at) **\<Type>** 之物件的引數時，將會間接建構 valarray 的子集。 會指定從父 valarray 選取之子集的預存值包括：

- valarray 中的起始索引。

- 總長度，或配量中的項目數。

- 分散，或 valarray 中後續索引之間的距離。

如果配量定義的集合是常數 valarray 的子集，則配量會是新的 valarray。 如果配量定義的集合是非常數 valarray 的子集，則配量會有原始 valarray 的參考語意。 非常數 valarrays 的評估機制可節省時間和記憶體。

只有在配量所定義的來源和目的地子集相異，且所有索引皆有效時，才能保證 valarray 的作業。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[slice](#slice)|定義 `valarray` 的子集，其中包含等距且在指定項目開始的一些項目。|

### <a name="member-functions"></a>成員函式

|成員函式|說明|
|-|-|
|[size](#size)|尋找 `valarray` 之配量中的項目數。|
|[start](#start)|尋找 `valarray` 之配量的起始索引。|
|[stride](#stride)|尋找 `valarray` 之配量的元素之間的距離。|

## <a name="requirements"></a>需求

**標頭：** \<valarray>

**命名空間：** std

## <a name="size"></a>  slice::size

尋找 valarray 之配量中的項目數。

```cpp
size_t size() const;
```

### <a name="return-value"></a>傳回值

valarray 之配量中的項目數。

### <a name="example"></a>範例

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="slice"></a>  slice::slice

定義 valarray 的子集，其中包含等距且以指定項目開始的一些項目。

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>參數

*_StartIndex*\
子集中第一個項目的 valarray 索引。

*_Len*\
子集中的項目數。

*長足*\
子集中項目之間的距離。

### <a name="return-value"></a>傳回值

預設的建構函式會針對起始索引、總長度及分散儲存零。 第二個函式會儲存起始索引的 *_StartIndex* 、 *_Len*作為總長度, 以及 stride 的*stride* 。

### <a name="remarks"></a>備註

分散可能是負數。

### <a name="example"></a>範例

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="start"></a>  slice::start

尋找 valarray 之配量的起始索引。

```cpp
size_t start() const;
```

### <a name="return-value"></a>傳回值

valarray 之配量的起始索引。

### <a name="example"></a>範例

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="stride"></a>  slice::stride

尋找 valarray 之配量中項目之間的距離。

```cpp
size_t stride() const;
```

### <a name="return-value"></a>傳回值

valarray 之配量中項目之間的距離。

### <a name="example"></a>範例

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
