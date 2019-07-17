---
title: less 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::less
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
ms.openlocfilehash: 13aef35856066f9c1897c3d8855c5ff537aa3567
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245342"
---
# <a name="less-struct"></a>less 結構

二元述詞執行小於-運算 (`operator<`) 在其引數。

## <a name="syntax"></a>語法

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*\
支援 `operator<` 的任何類型，其接受指定或推斷類型的運算元。

*左邊*\
小於運算的左運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*權限*\
小於運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

## <a name="return-value"></a>傳回值

`Left < Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator<` 所傳回的類型。

## <a name="remarks"></a>備註

二元述詞`less` < `Type`> 提供嚴格弱式順序的一組項目值的型別*類型*成等價類別，如果且只有此類型滿足數學標準因此要排序的需求。 任何指標類型的特製化都會產生元素的總排序，其中所有不同值的元素都會依照彼此的相關順序排序。

## <a name="example"></a>範例

```cpp
// functional_less.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

struct MyStruct {
   MyStruct(int i) : m_i(i){}

   bool operator < (const MyStruct & rhs) const {
      return m_i < rhs.m_i;
   }

   int m_i;
};

int main() {
   using namespace std;
   vector <MyStruct> v1;
   vector <MyStruct>::iterator Iter1;
   vector <MyStruct>::reverse_iterator rIter1;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
       v1.push_back( MyStruct(rand()));

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   sort( v1.begin( ), v1.end( ), less<MyStruct>());

   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```
