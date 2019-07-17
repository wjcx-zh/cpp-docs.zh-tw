---
title: pair 結構
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: f372ae036ff4843532efa18c3d518820b5f06111
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244423"
---
# <a name="pair-structure"></a>pair 結構

提供可將兩個物件視為單一物件之功能的結構。

## <a name="syntax"></a>語法

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>參數

*val1*\
值，初始化 `pair` 第一個項目。

*Val2*\
值，初始化 `pair` 第二個項目。

*權限*\
配對，其值要用來初始化另一個配對的項目。

## <a name="return-value"></a>傳回值

第一個 （預設） 建構函式初始化的類型為預設值組的第一個項目`T1`並且將第二個項目類型的預設`T2`。

第二個建構函式會初始化至配對的第一個項目*Val1*和第二個*Val2。*

第三個 (範本) 建構函式會初始化該配對的第一個項目為 `Right`. **first** 和第二個項目為 `Right`. **second**。

第四個建構函式會初始化至配對的第一個項目*Val1*和第二個*Val2*使用[右值參考宣告子： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="remarks"></a>備註

範本結構會儲存一組物件的型別`T1`和`T2`分別。 型別`first_type`等同於範本參數`T1`並輸入`second_type`等同於範本參數`T2`。 `T1` 和`T2`各自需要提供只有預設建構函式、 單一引數建構函式和解構函式。 類型 `pair` 的所有成員是公用的，因為該類型宣告為 `struct`，而不是 **class**。 配對最常見的兩種用途是當作函式的傳回類型，這些函式會傳回兩個值，以及當作關聯容器類別 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)的項目，這些類別都具有與每個項目相關聯的索引鍵和實值類型。 後者滿足成對關聯容器的需求，也具有 `pair`< **const**`key_type`, `mapped_type`> 形式的實值類型。

## <a name="example"></a>範例

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
