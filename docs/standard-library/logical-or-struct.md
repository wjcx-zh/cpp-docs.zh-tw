---
title: logical_or 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_or
helpviewer_keywords:
- logical_or class
- logical_or struct
ms.assetid: ec8143f8-5755-4e7b-8025-507fb6bf6911
ms.openlocfilehash: ec3637c1d5a2d0d916aec012783cecd37a179468
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246453"
---
# <a name="logicalor-struct"></a>logical_or 結構

在其引數上執行邏輯分離運算 ( `operator||`) 的預先定義函式物件。

## <a name="syntax"></a>語法

```
template <class Type = void>
struct logical_or : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator||
template <>
struct logical_or<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) || std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*\
支援 `operator||` 的任何類型，其接受指定或推斷類型的運算元。

*左邊*\
邏輯分離運算的左運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*權限*\
邏輯分離運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

## <a name="return-value"></a>傳回值

`Left || Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator||` 所傳回的類型。

## <a name="remarks"></a>備註

針對使用者定義的類型，並沒有任何最少運算的運算元評估。 兩個引數都是由 `operator||` 評估。

## <a name="example"></a>範例

```cpp
// functional_logical_or.cpp
// compile with: /EHsc
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque <bool> d1, d2, d3( 7 );
   deque <bool>::iterator iter1, iter2, iter3;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      d1.push_back((bool)((rand() % 2) != 0));
   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      d2.push_back((bool)((rand() % 2) != 0));
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   cout << "Original deque:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;

   // To find element-wise disjunction of the truth values
   // of d1 & d2, use the logical_or function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_or<bool>( ) );
   cout << "The deque which is the disjuction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true false false true false false )
Original deque:
d2 = ( false false false true true true true )
The deque which is the disjuction of d1 & d2 is:
d3 = ( true true false true true true true )
```
