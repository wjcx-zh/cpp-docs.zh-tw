---
title: greater_equal 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater_equal
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
ms.openlocfilehash: f09364203c905407d8ce4607f527d58108eec778
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243749"
---
# <a name="greaterequal-struct"></a>greater_equal 結構

執行更新版本比-或-等於運算的二元述詞 (`operator>=`) 在其引數。

## <a name="syntax"></a>語法

```cpp
template <class Type = void>
struct greater_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator>=
template <>
struct greater_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left)>= std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*\
支援 `operator>=` 的任何類型，其接受指定或推斷類型的運算元。

*左邊*\
大於或等於運算的左運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*權限*\
大於或等於運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

## <a name="return-value"></a>傳回值

`Left >= Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator>=` 所傳回的類型。

## <a name="remarks"></a>備註

二元述詞`greater_equal` < `Type`> 提供嚴格弱式順序的一組項目值的型別*類型*成等價類別，如果且只有此類型滿足數學標準因此要排序的需求。 任何指標類型的特製化都會產生元素的總排序，其中所有不同值的元素都會依照彼此的相關順序排序。

## <a name="example"></a>範例

```cpp
// functional_greater_equal.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater_equal<int>( )
   sort( v1.begin( ), v1.end( ), greater_equal<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (6262 6262 41 18467 6334 26500 19169)
Sorted vector v1 = (41 6262 6262 6334 18467 19169 26500)
Resorted vector v1 = (26500 19169 18467 6334 6262 6262 41)
```
