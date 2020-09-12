---
title: pair 結構
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: 6ccbea23835326d1e1840d8454f86c0eb72a5a7d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042052"
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

*Val1*\
值，初始化 `pair` 第一個項目。

*Val2*\
值，初始化 `pair` 第二個項目。

*對*\
配對，其值要用來初始化另一個配對的項目。

## <a name="return-value"></a>傳回值

第一個 (預設) 的函式會將該配對的第一個元素初始化為類型的預設值 `T1` ，並將第二個專案初始化為類型的預設值 `T2` 。  如果這兩種類型都是預設值，就會定義它可建構。

第二個函式會將配對的第一個元素初始化為 *Val1* ，而第二個則初始化為 *Val2。*  如果這兩種類型都是複製可建構，則會定義它。

第三個 (範本) 的函式會將該配對的第一個專案初始化為 `Right` 。 **第一個** 和第二個至 `Right` 。 **第二個**。  如果這兩個配對類型都是從提供的實值型別可建構，則會定義它。


第四個函式會將該配對的第一個專案初始化為 *Val1* ，而第二個則是使用右值參考宣告子來 *Val2* [：  &&](../cpp/rvalue-reference-declarator-amp-amp.md)。  如果這兩個配對類型都是從提供的實值型別可建構，則會定義它。

## <a name="remarks"></a>備註

範本結構會分別儲存一組類型的物件 `T1` 和 `T2` 。 此類型與樣板 `first_type` 參數相同 `T1` ，且類型與 `second_type` 範本參數相同 `T2` 。 `T1` 而且 `T2` 每個都只需要提供預設的函式、單一引數的函式，以及一個函式。 型別的所有成員 `pair` 都是公用的，因為型別是宣告為， **`struct`** 而不是 **`class`** 。 配對最常見的兩種用途是當作函式的傳回類型，這些函式會傳回兩個值，以及當作關聯容器類別 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)的項目，這些類別都具有與每個項目相關聯的索引鍵和實值類型。 後者滿足成對關聯容器的需求，而且具有表單的實數值型別 `pair< const key_type, mapped_type >` 。

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
