---
title: gslice 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5c47f91a3e029175d40bd1a762fb6e6ff527ee7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955810"
---
# <a name="gslice-class"></a>gslice 類別

valarray 的一個公用程式類別，用來定義 valarray 的多維度子集。 如果 valarray 被視為含有陣列中所有元素的多維度矩陣，則配量會從多維度陣列中擷取向量。

## <a name="remarks"></a>備註

此類別會儲存用來描述 [gslice_array](../standard-library/gslice-array-class.md) 類型之物件特性的參數。 當 gslice 類別的物件是作為 [valarray](../standard-library/valarray-class.md#op_at)**\<Type>** 類別之物件的引數時，會間接建構 valarray 的子集。 會指定從父 valarray 選取之子集的預存值包括：

- 起始索引。

- 類別的長度向量`valarray<size_t>`。

- 類別的跨度向量`valarray<size_t>`。

兩個向量的長度必須相同。

如果 gslice 定義的集合是常數 valarray 的子集，則 gslice 會是新的 valarray。 如果 gslice 定義的集合是非常數 valarray 的子集，則 gslice 會有原始 valarray 的參考語意。 非常數 valarrays 的評估機制可節省時間和記憶體。

只有在 gslice 所定義的來源和目的地子集相異，且所有索引皆有效時，才能保證 valarray 的作業。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[gslice](#gslice)|定義 `valarray` 的子集，其中包含 `valarray` 的多個配量 (全都起始於指定的元素)。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[size](#size)|尋找指定 `valarray` 之一般配量中的元素數的陣列值。|
|[start](#start)|尋找 `valarray` 之一般配量的起始索引。|
|[stride](#stride)|尋找 `valarray` 之一般配量的元素之間的距離。|

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

## <a name="gslice"></a>  gslice::gslice

valarray 的一個公用程式類別，用來定義 valarray 的多維度切割。

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>參數

*_StartIndex* valarray 索引子集的第一個元素。

*_LenArray*每個配量中指定的項目數的陣列。

*_IncArray*指定在每個配量的跨度的陣列。

### <a name="return-value"></a>傳回值

預設建構函式會針對起始索引儲存零，以及針對長度和跨度向量儲存零長度向量。 第二個建構函式儲存 *_StartIndex*起始的索引，如 *_LenArray*針對長度陣列，並 *_IncArray*針對跨度陣列。

### <a name="remarks"></a>備註

**gslice** 會定義 valarray 的子集，此子集由該 valarray 的多個配量所構成，其中每個配量都起始於相同的指定元素。 使用陣列來定義多個配量的能力是 `gslice` 與 [slice::slice](../standard-library/slice-class.md#slice) 之間唯一的差異。 第一個配量會有索引的第一個項目 *_StartIndex*，第一個項目所指定項目數目 *_LenArray*，和第一個元素的跨度 *_IncArray*. 下一組正交配量的第一個元素會由第一個配量指定。 第二個元素 *_LenArray*指定元素數目。 第二個項目所指定步距 *_IncArray*。 配量的第三維度會以二維陣列的元素作為起始元素，然後以類似的方式繼續進行

### <a name="example"></a>範例

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="size"></a>  gslice::size

尋找指定 valarray 之一般配量中元素數目的陣列值。

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>傳回值

指定 valarray 之一般配量的每個配量中元素數目的 valarray。

### <a name="remarks"></a>備註

此成員函式會傳回預存的配量長度。

### <a name="example"></a>範例

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
 vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="start"></a>  gslice::start

尋找 valarray 之一般配量的起始索引。

```cpp
size_t start() const;
```

### <a name="return-value"></a>傳回值

valarray 之一般配量的起始索引。

### <a name="example"></a>範例

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="stride"></a>  gslice::stride

尋找 valarray 之一般配量中元素之間的距離。

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>傳回值

指定 valarray 之一般配量的每個配量中元素間距離的 valarray。

### <a name="example"></a>範例

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
 vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
