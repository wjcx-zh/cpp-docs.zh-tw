---
title: equal_to 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::equal_to
helpviewer_keywords:
- equal_to function
- equal_to struct
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
ms.openlocfilehash: ac7c5a3ed8d85e6ea3ad46ec61c7968bc19cd15e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245839"
---
# <a name="equalto-struct"></a>equal_to 結構

執行等號比較運算的二元述詞 (`operator==`) 在其引數。

## <a name="syntax"></a>語法

```cpp
template <class Type = void>
struct equal_to : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator==
template <>
struct equal_to<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
      ->  decltype(std::forward<T>(Left) == std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*\
支援 `operator==` 的任何類型，其接受指定或推斷類型的運算元。

*左邊*\
等號比較運算的左運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*權限*\
等號比較運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

## <a name="return-value"></a>傳回值

`Left == Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator==` 所傳回的類型。

## <a name="remarks"></a>備註

類型的物件*型別*必須能進行相等比較。 在物件集合上定義的 `operator==` 必須符合等價關聯的數學屬性，才能進行此作業。 所有內建的數字和指標類型皆符合這項需求。

## <a name="example"></a>範例

```cpp
// functional_equal_to.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 ( 6 );
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i+=2 )
   {
      v1.push_back( 2.0 *i );
      v1.push_back( 2.0 * i + 1.0 );
   }

   int j;
   for ( j = 0 ; j <= 5 ; j+=2 )
   {
      v2.push_back( - 2.0 * j );
      v2.push_back( 2.0 * j + 1.0 );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Testing for the element-wise equality between v1 & v2
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      equal_to<double>( ) );

   cout << "The result of the element-wise equal_to comparison\n"
      << "between v1 & v2 is: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 0 1 4 5 8 9 )
The vector v2 = ( -0 1 -4 5 -8 9 )
The result of the element-wise equal_to comparison
between v1 & v2 is: ( 1 1 0 1 0 1 )
```
