---
title: less_equal 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::less_equal
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
ms.openlocfilehash: 67a686b139ae4abbf25a42a994cceaba008decf5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245376"
---
# <a name="lessequal-struct"></a>less_equal 結構

執行無比-或-等於運算的二元述詞 (`operator<=`) 在其引數。

## <a name="syntax"></a>語法

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*\
支援 `operator<=` 的任何類型，其接受指定或推斷類型的運算元。

*左邊*\
小於或等於運算的左運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*權限*\
小於或等於運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

## <a name="return-value"></a>傳回值

`Left <= Right` 的結果。 此特製化範本會完整轉送結果 (具有 `operator<=` 所傳回的類型)。

## <a name="remarks"></a>備註

二元述詞`less_equal` < `Type`> 提供嚴格弱式順序的一組項目值的型別*類型*成等價類別，如果且只有此類型滿足數學標準因此要排序的需求。 任何指標類型的特製化都會產生元素的總排序，其中所有不同值的元素都會依照彼此的相關順序排序。

## <a name="example"></a>範例

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
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
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```
