---
title: multiset 類別
ms.date: 11/04/2016
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
ms.openlocfilehash: 83980094562e1c0083a879d1dc9aab591dc52d02
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419830"
---
# <a name="multiset-class"></a>multiset 類別

「C++ 標準程式庫」multiset 類別可用來在集合中儲存及擷取資料，其中集合中所含的元素值不需要是唯一的，而且會作為自動排序資料時所依據的索引鍵值。 多重集中項目的索引鍵值不能直接變更。 相反地，必須刪除舊值，並插入具有新值的項目。

## <a name="syntax"></a>語法

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>參數

*金鑰*\
要存放在多重集中的項目資料類型。

*比較*\
類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在多重集中的相對順序。 二元述詞 **less**\<Key> 是預設值。

在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)。

配置*器\*
代表預存配置器物件的類型，封裝有關多重集之記憶體配置和解除配置的詳細資訊。 預設值是 `allocator<Key>`。

## <a name="remarks"></a>備註

「C++ 標準程式庫」multiset 類別是：

- 關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。

- 可逆轉的，因為它提供雙向的迭代器以存取其項目。

- 已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。

- 多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目值。

- 簡單關聯的容器，因為其項目值是其索引鍵值的。

- 類別樣板，因為它提供的功能是泛型，因此獨立于包含做為元素的特定資料類型。 使用的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。

multiset 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#insert) 和 [multiset](#multiset) 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的一組需求，因此，使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是一組基本功能，不過，已足以在類別成員函式的內容中有意義地溝通迭代器範圍 [ `First`, `Last`)。

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 關聯的容器已針對查閱、插入和移除作業最佳化。 明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。

當關聯值與其索引鍵的條件由應用程式滿足時，多重集應該是首選的關聯容器。 多重集的項目可以是多重，並當做自己的排序鍵，因此索引鍵不是唯一的。 例如，這種結構的模型是文字的已排序清單，其中文字可以出現多次。 如果不允許文字的多個項目，則集合是適當的容器結構。 如果唯一定義做為值附加至唯一關鍵字清單，則對應是包含這個資料的適當結構。 如果定義不是唯一的，則多重對應是首選容器。

多重集會藉由呼叫類型為*Compare*的預存函式物件，排序它所控制的序列。 這個預存物件是可藉由呼叫成員函式 [key_comp](#key_comp) 來存取的比較函式。 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 *f*( *x*, *y*) 是有兩個引數物件 *x* 和 *y* 以及傳回值 **true** 或 **false** 的函式物件。 如果二元述詞是非自反、反對稱性且可轉移的，而且如果等價是可轉移的，其中兩個物件 x 和 y 是定義為當 *f*( *x,y*) 和 *f*( *y,x*) 皆為 false 時即相等，則施加於集合的排序是嚴格弱式排序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。

在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[multiset](#multiset)|建構一個空的 `multiset`，或是指定之 `multiset` 的全部或部分複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|`allocator` 物件之 `multiset` 類別的 typedef。|
|[const_iterator](#const_iterator)|雙向反覆運算器的 typedef，可以讀取 `multiset`中的**const**元素。|
|[const_pointer](#const_pointer)|`multiset`中**const**元素的指標的 typedef。|
|[const_reference](#const_reference)|對儲存在 `multiset` 中以讀取和執行**const**運算之**const**元素的參考的 typedef。|
|[const_reverse_iterator](#const_reverse_iterator)|雙向反覆運算器的 typedef，可以讀取 `multiset`中的任何**const**元素。|
|[difference_type](#difference_type)|範圍 (介於迭代器所指的項目) 中 `multiset` 的項目數量的帶正負號整數 typedef。|
|[iterator](#iterator)|雙向迭代器的 typedef，可以讀取或修改 `multiset` 中的任何項目。|
|[key_compare](#key_compare)|函式物件之 typedef，可比較兩個索引鍵以判斷兩個項目在 `multiset` 中的相對順序。|
|[key_type](#key_type)|函式物件之 typedef，可比較兩個排序鍵以判斷兩個項目在 `multiset` 中的相對順序。|
|[pointer](#pointer)|在 `multiset` 中指向項目的指標之 typedef。|
|[reference](#reference)|`multiset` 中預存項目的參考之 typedef。|
|[reverse_iterator](#reverse_iterator)|雙向迭代器的 typedef，可以讀取或修改反轉 `multiset` 中的項目。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `multiset` 中的項目數。|
|[value_compare](#value_compare)|可將兩個項目做為排序鍵進行比較之函式物件的 typedef，以判斷項目在 `multiset` 中的相對順序。|
|[value_type](#value_type)|typedef，在做為值的產能上，描述做為 `multiset` 的項目儲存的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[begin](#begin)|傳回指向 `multiset` 中的第一個項目的迭代器。|
|[cbegin](#cbegin)|傳回常數迭代器，為 `multiset` 中的第一個項目定址。|
|[cend](#cend)|傳回常數迭代器，為 `multiset` 中最後一個項目的下一個位置定址。|
|[清除](#clear)|清除 `multiset` 的所有項目。|
|[計數](#count)|傳回 `multiset` 中索引鍵符合指定為參數之索引鍵的項目數目。|
|[crbegin](#crbegin)|傳回常數迭代器，為反轉集合中的第一個項目定址。|
|[crend](#crend)|傳回常數迭代器，為反轉集合中最後一個項目的下一個位置定址。|
|[emplace](#emplace)|將就地建構的項目插入 `multiset` 中。|
|[emplace_hint](#emplace_hint)|將就地建構的項目 (含位置提示) 插入 `multiset` 中。|
|[empty](#empty)|測試 `multiset` 是否為空白。|
|[end](#end)|傳回 `multiset` 中，指向最後一個項目後面的位置之迭代器。|
|[equal_range](#equal_range)|傳回一對迭代器。 配對中第一個迭代器指向 `multiset` 中索引鍵大於指定索引鍵的第一個項目。 配對中第二個迭代器指向 `multiset` 中索引鍵等於或大於指定索引鍵的第一個項目。|
|[erase](#erase)|從指定的位置移除 `multiset` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|
|[find](#find)|傳回迭代器，指向 `multiset` 中索引鍵等於指定索引鍵的第一個項目的位置。|
|[get_allocator](#get_allocator)|傳回用來建構 `allocator` 的 `multiset` 物件複本。|
|[insert](#insert)|將項目或項目範圍插入至 `multiset`。|
|[key_comp](#key_comp)|提供可比較兩個排序鍵的函式物件，以判斷兩個項目在 `multiset` 中的相對順序。|
|[lower_bound](#lower_bound)|傳回迭代器，指向 `multiset` 中索引鍵等於或大於特定索引鍵的第一個項目。|
|[max_size](#max_size)|傳回 `multiset` 的最大長度。|
|[rbegin](#rbegin)|傳回指向反轉 `multiset` 中的第一個項目的迭代器。|
|[rend](#rend)|傳回反轉 `multiset` 中，指向最後一個項目的下一個位置之迭代器。|
|[size](#size)|傳回 `multiset` 中的項目數目。|
|[swap](#swap)|交換兩個 `multiset` 的項目。|
|[upper_bound](#upper_bound)|傳回迭代器，指向 `multiset` 中索引鍵大於特定索引鍵的第一個項目。|
|[value_comp](#value_comp)|擷取 `multiset` 中用於排序項目值的比較物件之複本。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|用另一個 `multiset` 的複本取代 `multiset` 的項目。|

## <a name="requirements"></a>需求

**標頭：** \<設定 >

**命名空間:** std

## <a name="allocator_type"></a>  multiset::allocator_type

一種類型，代表 multiset 物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>備註

`allocator_type` 與樣板參數 `Allocator` 同義。

如需有關 `Allocator` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](#get_allocator)get_allocator`allocator_type` 的範例。

## <a name="begin"></a>  multiset::begin

傳回迭代器，定址對象是 multiset 中的第一個元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 multiset 中的第一個元素，或空 multiset 後面的位置。

### <a name="example"></a>範例

```cpp
// multiset_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::const_iterator ms1_cIter;

   ms1.insert( 1 );
   ms1.insert( 2 );
   ms1.insert( 3 );

   ms1_Iter = ms1.begin( );
   cout << "The first element of ms1 is " << *ms1_Iter << endl;

   ms1_Iter = ms1.begin( );
   ms1.erase( ms1_Iter );

   // The following 2 lines would err as the iterator is const
   // ms1_cIter = ms1.begin( );
   // ms1.erase( ms1_cIter );

   ms1_cIter = ms1.begin( );
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;
}
```

```Output
The first element of ms1 is 1
The first element of ms1 is now 2
```

## <a name="cbegin"></a>  multiset::cbegin

傳回**常數**反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**Const**雙向存取反覆運算器，指向範圍的第一個專案，或指向空白範圍結尾之外的位置（針對空白範圍，`cbegin() == cend()`）。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如以下範例所示。 在此範例中，請將 `Container` 視為支援 `begin()` 和 `cbegin()`之任何種類的可修改（非**const**）容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multiset::cend

傳回**常數**反覆運算器，定址範圍中最後一個元素之後的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的**const**雙向存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如以下範例所示。 在此範例中，請將 `Container` 視為支援 `end()` 和 `cend()`之任何種類的可修改（非**const**）容器。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a>  multiset::clear

清除 multiset 的所有元素。

```cpp
void clear();
```

### <a name="example"></a>範例

```cpp
// multiset_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 1 );
   ms1.insert( 2 );

   cout << "The size of the multiset is initially "
        << ms1.size( ) << "." << endl;

   ms1.clear( );
   cout << "The size of the multiset after clearing is "
        << ms1.size( ) << "." << endl;
}
```

```Output
The size of the multiset is initially 2.
The size of the multiset after clearing is 0.
```

## <a name="const_iterator"></a>  multiset::const_iterator

一種類型，提供可讀取 multiset 中 **const** 元素的雙向迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](#begin)begin`const_iterator` 的範例。

## <a name="const_pointer"></a>  multiset::const_pointer

一種類型，提供 multiset 中 **const** 元素的指標。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 multiset 物件中的元素。

## <a name="const_reference"></a>  multiset::const_reference

一種類型，提供對儲存在 multiset 中以供讀取和執行 **const** 運算之 **const** 元素的參考。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>範例

```cpp
// multiset_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator

一種類型，提供可讀取 multiset 中任何 **const** 元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 multiset。

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#rend)rend`const_reverse_iterator` 的範例。

## <a name="count"></a>  multiset::count

傳回 multiset 中索引鍵符合參數指定之索引鍵的項目數。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>參數

*金鑰*\
要從 multiset 中比對之項目的索引鍵。

### <a name="return-value"></a>傳回值

multiset 中排序索引鍵符合參數索引鍵的項目數。

### <a name="remarks"></a>備註

成員函式會傳回下列範圍中的元素數目 *x*

\[ lower_bound （索引*鍵*）、upper_bound （索引*鍵*））

### <a name="example"></a>範例

下列範例示範如何使用 multiset::count 成員函式。

```cpp
// multiset_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    multiset<int> ms1;
    multiset<int>::size_type i;

    ms1.insert(1);
    ms1.insert(1);
    ms1.insert(2);

    // Elements do not need to be unique in multiset,
    // so duplicates are allowed and counted.
    i = ms1.count(1);
    cout << "The number of elements in ms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = ms1.count(2);
    cout << "The number of elements in ms1 with a sort key of 2 is: "
         << i << "." << endl;

    i = ms1.count(3);
    cout << "The number of elements in ms1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in ms1 with a sort key of 1 is: 2.
The number of elements in ms1 with a sort key of 2 is: 1.
The number of elements in ms1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multiset::crbegin

傳回 const 迭代器，用於定址反轉 Multiset 中的第一個項目。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

const 反向雙向迭代器，用於定址反轉 Multiset 中的第一個元素，或用於定址未反轉 Multiset 中的最後一個元素。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 multiset 搭配使用，就如同 begin 是與 multiset 搭配使用一樣。

有 `crbegin`的傳回值時，無法修改 Multiset 物件。

`crbegin` 可用來向後逐一查看 multiset。

### <a name="example"></a>範例

```cpp
// multiset_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

```Output
The first element in the reversed multiset is 30.
```

## <a name="crend"></a>  multiset::crend

傳回常數迭代器，定址對象是反轉 multiset 中最後一個元素後面的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 multiset 中最後一個元素後面的位置 (未反轉 multiset 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 multiset 搭配使用，就如同 [end](#end) 是與 multiset 搭配使用一樣。

有 `crend`的傳回值時，無法修改 Multiset 物件。

`crend` 可以用來測試反轉迭代器是否已到達其 multiset 的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// multiset_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crend( ) ;
   ms1_crIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>  multiset::difference_type

一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 multiset 的元素數目。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 `first` 和 `last` 之間範圍 [ `first`, `last`) 內的元素數目，包括 `first` 所指的元素以及上限到 `last` 所指元素 (但不包含此元素) 的元素範圍。

請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別，但只有隨機存取容器 (例如 vector) 所提供的隨機存取迭代器，才支援迭代器之間的減法。

### <a name="example"></a>範例

```cpp
// multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;

   ms1.insert( 20 );
   ms1.insert( 10 );
   ms1.insert( 20 );

   ms1_bIter = ms1.begin( );
   ms1_eIter = ms1.end( );

   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );

   // The keys, and hence the elements, of a multiset are not unique
   cout << "The number '5' occurs " << df_typ5
        << " times in multiset ms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in multiset ms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in multiset ms1.\n";

   // Count the number of elements in a multiset
   multiset <int>::difference_type  df_count = 0;
   ms1_Iter = ms1.begin( );
   while ( ms1_Iter != ms1_eIter)
   {
      df_count++;
      ms1_Iter++;
   }

   cout << "The number of elements in the multiset ms1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in multiset ms1.
The number '10' occurs 1 times in multiset ms1.
The number '20' occurs 2 times in multiset ms1.
The number of elements in the multiset ms1 is: 3.
```

## <a name="emplace"></a>  multiset::emplace

插入就地建構元素 (沒有執行複製或移動作業)，其中含位置提示。

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*引數*|轉送以建構要插入到 multiset 中之元素的引數。|

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

在定位期間，如果擲回例外狀況，就不會修改容器的狀態。

### <a name="example"></a>範例

```cpp
// multiset_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    multiset<string> s1;

    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;

    s1.emplace("Bob");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="emplace_hint"></a>  multiset::emplace_hint

插入就地建構元素 (沒有執行複製或移動作業)，其中含位置提示。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*引數*|轉送以建構要插入到 multiset 中之元素的引數。|
|*where*|要開始搜尋正確的插入點的地方。 （如果該點緊接在*位置*之前，則會在分攤常數時間中進行插入，而不是對數時間）。|

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

在定位期間，如果擲回例外狀況，就不會修改容器的狀態。

如需程式碼範例，請參閱 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)。

## <a name="empty"></a>  multiset::empty

測試 multiset 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果 multiset 是空的，即為 **true**；如果 multiset 不是空的，則為 **false**。

### <a name="example"></a>範例

```cpp
// multiset_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2;
   ms1.insert ( 1 );

   if ( ms1.empty( ) )
      cout << "The multiset ms1 is empty." << endl;
   else
      cout << "The multiset ms1 is not empty." << endl;

   if ( ms2.empty( ) )
      cout << "The multiset ms2 is empty." << endl;
   else
      cout << "The multiset ms2 is not empty." << endl;
}
```

```Output
The multiset ms1 is not empty.
The multiset ms2 is empty.
```

## <a name="end"></a>  multiset::end

傳回超出結尾 (past-the-end) 迭代器。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

超出結尾迭代器。 如果 multiset 是空的，則 `multiset::end() == multiset::begin()`。

### <a name="remarks"></a>備註

**end** 是用來測試迭代器是否已超過其 multiset 的結尾。

**end** 所傳回的值不應該被取值。

如需程式碼範例，請參閱 [multiset::find](#find)。

## <a name="equal_range"></a>  multiset::equal_range

傳回一組迭代器，分別指向 multiset 中索引鍵大於指定索引鍵的第一個元素，以及指向 multiset 中索引鍵等於或大於該索引鍵的第一個元素。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>參數

*金鑰*\
要與所搜尋之 multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

一組迭代器，其中第一個是索引鍵的 [lower_bound](#lower_bound)，第二個是索引鍵的 [upper_bound](#upper_bound)。

若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之 `pr` 配對的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。

### <a name="example"></a>範例

```cpp
// multiset_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multiset<int, less<int> > IntSet;
   IntSet ms1;
   multiset <int> :: const_iterator ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = ms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.second ) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.first ) << "." << endl;

   // Compare the upper_bound called directly
   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *ms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = ms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key less than 40." << endl;
   else
      cout << "The element of multiset ms1 with a key >= 40 is: "
                << *( p1.first ) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The multiset ms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  multiset::erase

從 multiset 中指定的位置移除某個元素或某個範圍的元素，或移除符合指定索引鍵的元素。

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>參數

*Where*\
要移除之項目的位置。

*第一個*\
要移除之第一個項目的位置。

*上次*\
緊接在要移除之最後一個項目後面的位置。

*金鑰*\
要移除之項目的索引鍵值。

### <a name="return-value"></a>傳回值

針對前兩個成員函式，會傳回雙向迭代器，其中指定任何移除之元素後剩餘的第一個元素，或如果沒有這類元素，則傳回 multiset 結尾的元素。

針對第三個成員函式，會傳回已從 multiset 移除的元素數目。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [set::erase](../standard-library/set-class.md#erase)。

## <a name="find"></a>  multiset::find

傳回迭代器，其表示 multiset 中索引鍵等於指定索引鍵的元素的位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>參數

*金鑰*\
要以所搜尋之 multiset 中元素的排序鍵比對的索引鍵值。

### <a name="return-value"></a>傳回值

迭代器，參考對象是具有指定索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，則是 multiset 中最後一個元素後面的位置 ( `multiset::end()`)。

### <a name="remarks"></a>備註

此成員函式會傳回反覆運算器，它會參考多重集中的專案，其索引鍵等同于二元述詞下的引數索引*鍵*，而此二元述詞會根據小於可比較性的關聯來引發排序。

如果 `find` 的傳回值指派給 `const_iterator`，則無法修改多重集物件。 如果 `find` 的傳回值指派給 `iterator`，則可修改多重集物件

### <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    multiset<int> s1({ 40, 45 });
    cout << "The starting multiset s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified multiset s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a>  multiset::get_allocator

傳回一份用來建構 multiset 的配置器物件複本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

multiset 所使用的配置器。

### <a name="remarks"></a>備註

multiset 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器，足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// multiset_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int>::allocator_type ms1_Alloc;
   multiset <int>::allocator_type ms2_Alloc;
   multiset <double>::allocator_type ms3_Alloc;
   multiset <int>::allocator_type ms4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multiset <int> ms1;
   multiset <int, allocator<int> > ms2;
   multiset <double, allocator<double> > ms3;

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms3.max_size( ) <<  "." << endl;

   // The following lines create a multiset ms4
   // with the allocator of multiset ms1
   ms1_Alloc = ms1.get_allocator( );
   multiset <int> ms4( less<int>( ), ms1_Alloc );
   ms4_Alloc = ms4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( ms1_Alloc == ms4_Alloc )
   {
      cout << "Allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "Allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  multiset::insert

將某個元素或元素範圍插入 multiset 中。

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*初始值*|要插入至 multiset 的元素值。|
|*其中*|要開始搜尋正確的插入點的地方。 （如果該點緊接在*位置*之前，則會在分攤常數時間中進行插入，而不是對數時間）。|
|*ValTy*|範本參數，指定多重集可用來建立[value_type](../standard-library/map-class.md#value_type)之元素的引數類型，並將*Val*當做引數完美轉送。|
|*第一個*|要複製之第一個元素的位置。|
|*最後一個*|要複製之最一個元素後方的位置。|
|*InputIterator*|符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#value_type) 物件的類型。|
|*IList*|要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。|

### <a name="return-value"></a>傳回值

單一元素插入成員函式 (1) 和 (2)，會將迭代器傳回至在 multiset 中插入新元素的位置。

具有提示的單一元素成員函式 (3) 和 (4)，會傳回迭代器，其指向在 multiset 中插入新元素的位置。

### <a name="remarks"></a>備註

此函式不會使指標或參考無效，但是可能會使容器的所有迭代器無效。

在只插入一個元素的期間，若擲出例外狀況，則不會修改容器的狀態。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。

容器的 [value_type](../standard-library/map-class.md#value_type) 是屬於容器的 typedef，而針對 set，`multiset<V>::value_type` 是類型 `const V`。

範圍成員函式 (5) 會將元素值序列插入至 multiset，而 multiset 對應至範圍 `[First, Last)` 中迭代器指定的每個元素；因此不會插入 `Last`。 容器成員函式 `end()` 是指容器中最後一個元素後方的位置；例如，陳述式 `s.insert(v.begin(), v.end());` 會將 `v` 的所有元素插入至 `s`。

初始設定式清單成員函式 (6) 會使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 multiset。

針對插入就地建構 (也就是未執行任何複製或移動作業) 的元素，請參閱 [multiset::emplace](#emplace) 和 [multiset::emplace_hint](#emplace_hint)。

### <a name="example"></a>範例

```cpp
// multiset_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multiset<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original multiset values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    s1.insert(1);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multiset<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified multiset values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    multiset<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    multiset<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a>  multiset::iterator

一種類型，提供可讀取 multiset 中任何元素的常數[雙向迭代器](../standard-library/bidirectional-iterator-tag-struct.md)。

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>範例

如需如何宣告和使用 `iterator`的範例，請參閱[begin](#begin)的範例。

## <a name="key_comp"></a>  multiset::key_comp

擷取一份用來排序 multiset 中索引鍵的比較物件複本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 multiset 用來排序其項目的函式物件，亦即樣板參數 `Compare`。

如需有關 `Compare` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="remarks"></a>備註

預存物件會定義成員函式：

**bool 運算子**（ **const key &** *x*， **const key &** *y*）;

如果 *x* 在排序次序中絕對位於 *y* 的前面，此函式就會傳回 true。

請注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 都與範本參數 `Compare` 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

```cpp
// multiset_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of ms1."
           << endl;
   }

   multiset <int, greater<int> > ms2;
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.
```

## <a name="key_compare"></a>  multiset::key_compare

一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷 multiset 中兩個元素的相對順序。

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>備註

`key_compare` 與樣板參數 `Compare` 同義。

如需有關 `Compare` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#key_comp)key_comp`key_compare` 的範例。

## <a name="key_type"></a>  multiset::key_type

一種提供函式物件的類型，該函式物件可比較排序鍵來判斷 multiset 中兩個元素的相對順序。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

`key_type` 與樣板參數 `Key` 同義。

如需有關 `Key` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#value_type)value_type`key_type` 的範例。

## <a name="lower_bound"></a>  multiset::lower_bound

傳回迭代器，指向 multiset 中索引鍵等於或大於指定索引鍵的第一個元素。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>參數

*金鑰*\
要與所搜尋之 multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

`iterator` 或 `const_iterator`，用來定址多重集中索引鍵等於或大於引數索引鍵的元素位置，或者，如果找不到與索引鍵相符的專案，則定址多重集最後一個元素後面的位置。

### <a name="example"></a>範例

```cpp
// multiset_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.lower_bound( 20 );
   cout << "The element of multiset ms1 with a key of 20 is: "
        << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of multiset ms1 with a key of 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.end( );
   ms1_AcIter--;
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );
   cout << "The element of ms1 with a key matching "
        << "that of the last element is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The element of multiset ms1 with a key of 20 is: 20.
The multiset ms1 doesn't have an element with a key of 40.
The element of ms1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  multiset::max_size

傳回 multiset 的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

multiset 的最大可能長度。

### <a name="example"></a>範例

```cpp
// multiset_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::size_type i;

   i = ms1.max_size( );
   cout << "The maximum possible length "
        << "of the multiset is " << i << "." << endl;
}
```

## <a name="multiset"></a>  multiset::multiset

建構一個空的 multiset，或是某個其他 multiset 之全部或部分複本的 multiset。

```cpp
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*Al*|要用於此 multiset 物件的儲存體配置器類別，預設為 `Allocator`。|
|*背光*|類型為 `const Compare` 並用來排序 multiset 中元素的比較函式，預設為 `Compare`。|
|*Right*|要從中複製所建構之 multiset 的 multiset。|
|*第一個*|要複製的元素範圍中第一個元素的位置。|
|*最後一個*|超出要複製之元素範圍的第一個元素的位置。|
|*IList*|要從中複製項目的 initializer_list。|

### <a name="remarks"></a>備註

所有建構函式都會儲存一種配置器物件，此物件可管理 multiset 的記憶體儲存，且之後藉由呼叫 [get_allocator](#get_allocator) 即可傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。

所有建構函式都會將其 multiset 初始化。

所有建構函式都會儲存一個 Compare 類型的函式物件，此物件可用來在 multiset 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#key_comp) 即可傳回此物件。

前三個函式會指定空的初始多重集，第二個是指定要用來建立元素順序的比較函數（*Comp*）類型，而第三個是明確指定要使用的配置器類型（*Al*）。 關鍵字 **explicit** 會隱藏某些類型的自動類型轉換。

第四個函式會指定多重集*許可權*的複本。

第五個函式會藉由*向右*移動來指定多重集的複本。

第六、第七及第八個建構函式會指定 initializer_list 來從中複製元素。

接下來的三個建構函式會複製 multiset 的範圍 `[First, Last)`，其中會以越來越明確的方式指定比較函式及配置器的類型。

### <a name="example"></a>範例

```cpp
// multiset_ctor.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;

    // Create an empty multiset ms0 of key type integer
    multiset <int> ms0;

    // Create an empty multiset ms1 with the key comparison
    // function of less than, then insert 4 elements
    multiset <int, less<int> > ms1;
    ms1.insert(10);
    ms1.insert(20);
    ms1.insert(20);
    ms1.insert(40);

    // Create an empty multiset ms2 with the key comparison
    // function of greater than, then insert 2 elements
    multiset <int, less<int> > ms2;
    ms2.insert(10);
    ms2.insert(20);

    // Create a multiset ms3 with the
    // allocator of multiset ms1
    multiset <int>::allocator_type ms1_Alloc;
    ms1_Alloc = ms1.get_allocator();
    multiset <int> ms3(less<int>(), ms1_Alloc);
    ms3.insert(30);

    // Create a copy, multiset ms4, of multiset ms1
    multiset <int> ms4(ms1);

    // Create a multiset ms5 by copying the range ms1[ first,  last)
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;
    ms1_bcIter = ms1.begin();
    ms1_ecIter = ms1.begin();
    ms1_ecIter++;
    ms1_ecIter++;
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);

    // Create a multiset ms6 by copying the range ms4[ first,  last)
    // and with the allocator of multiset ms2
    multiset <int>::allocator_type ms2_Alloc;
    ms2_Alloc = ms2.get_allocator();
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);

    cout << "ms1 =";
    for (auto i : ms1)
        cout << " " << i;
    cout << endl;

    cout << "ms2 =";
    for (auto i : ms2)
        cout << " " << i;
   cout << endl;

   cout << "ms3 =";
   for (auto i : ms3)
       cout << " " << i;
    cout << endl;

    cout << "ms4 =";
    for (auto i : ms4)
        cout << " " << i;
    cout << endl;

    cout << "ms5 =";
    for (auto i : ms5)
        cout << " " << i;
    cout << endl;

    cout << "ms6 =";
    for (auto i : ms6)
        cout << " " << i;
    cout << endl;

    // Create a multiset by moving ms5
    multiset<int> ms7(move(ms5));
    cout << "ms7 =";
    for (auto i : ms7)
        cout << " " << i;
    cout << endl;

    // Create a multiset with an initializer_list
    multiset<int> ms8({1, 2, 3, 4});
    cout << "ms8=";
    for (auto i : ms8)
        cout << " " << i;
    cout << endl;
}
```

## <a name="op_eq"></a>  multiset::operator=

使用另一個 `multiset` 的項目來取代這個 `multiset` 的項目。

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*right*|要從中複製或移除元素的 `multiset`。|

### <a name="remarks"></a>備註

視所使用的參考型別（左值或右值）而定，`operator=` 會將元素複製或*移動到這個*`multiset`。 在這個位於 `multiset` 之前 `operator=` 中的所有元素都會被捨棄。

### <a name="example"></a>範例

```cpp
// multiset_operator_as.cpp
// compile with: /EHsc
#include <multiset>
#include <iostream>

int main( )
   {
   using namespace std;
   multiset<int> v1, v2, v3;
   multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  multiset::pointer

一種類型，提供 multiset 中元素的指標。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>備註

類型 **pointer** 可用來修改項目的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 multiset 物件中的元素。

## <a name="rbegin"></a>  multiset::rbegin

傳回迭代器，用於定址反轉 Multiset 中的第一個項目。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反向雙向迭代器，用於定址反轉 Multiset 中的第一個項目，或用於定址未反轉 Multiset 中的最後一個項目。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 multiset 搭配使用，就如同 begin 是與 multiset 搭配使用一樣。

如果 `rbegin` 的傳回值已指派給 `const_reverse_iterator`，則無法修改 Multiset 物件。 如果 `rbegin` 的傳回值已指派給 `reverse_iterator`，則可以修改 Multiset 物件。

`rbegin` 可用來向後逐一查看 multiset。

### <a name="example"></a>範例

```cpp
// multiset_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a multiset in a forward order
   cout << "The multiset is:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is:";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << " " << *ms1_rIter;
   cout << endl;

   // A multiset element can be erased by dereferencing to its key
   ms1_rIter = ms1.rbegin( );
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multiset is "<< *ms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed multiset is 30.
The multiset is: 10 20 30
The reversed multiset is: 30 20 10
After the erasure, the first element in the reversed multiset is 20.
```

## <a name="reference"></a>  multiset::reference

一種類型，提供對儲存在 multiset 中元素的參考。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>範例

```cpp
// multiset_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="rend"></a>  multiset::rend

傳回迭代器，定址對象是反轉 multiset 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 multiset 中最後一個元素後面的位置 (未反轉 multiset 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 multiset 搭配使用，就如同 [end](#end) 是與 multiset 搭配使用一樣。

如果 `rend` 的傳回值已指派給 `const_reverse_iterator`，則無法修改 Multiset 物件。 如果 `rend` 的傳回值已指派給 `reverse_iterator`，則可以修改 Multiset 物件。

`rend` 可以用來測試反轉迭代器是否已到達其 multiset 的結尾。

`rend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// multiset_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rend( ) ;
   ms1_rIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a multiset in a forward order
   cout << "The multiset is: ";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << *ms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is: ";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << *ms1_rIter << " ";
   cout << "." << endl;

   ms1_rIter = ms1.rend( );
   ms1_rIter--;
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rend( );
   --ms1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed multiset is " << *ms1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>  multiset::reverse_iterator

一種類型，提供可讀取或修改反轉 multiset 中元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 是用來反向逐一查看 multiset。

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#rbegin)rbegin`reverse_iterator` 的範例。

## <a name="size"></a>  multiset::size

傳回 multiset 中的元素數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

multiset 的目前長度。

### <a name="example"></a>範例

```cpp
// multiset_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: size_type i;

   ms1.insert( 1 );
   i = ms1.size( );
   cout << "The multiset length is " << i << "." << endl;

   ms1.insert( 2 );
   i = ms1.size( );
   cout << "The multiset length is now " << i << "." << endl;
}
```

```Output
The multiset length is 1.
The multiset length is now 2.
```

## <a name="size_type"></a>  multiset::size_type

一種不帶正負號的整數類型，可代表 multiset 中的元素數目。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#size)size`size_type` 的範例。

## <a name="swap"></a>  multiset::swap

交換兩個 multiset 的項目。

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*\
提供要與目標 multiset 交換之元素的引數 multiset。

### <a name="remarks"></a>備註

任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 multiset 中，成員函式就不會使其失效。

### <a name="example"></a>範例

```cpp
// multiset_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2, ms3;
   multiset <int>::iterator ms1_Iter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );
   ms2.insert( 100 );
   ms2.insert( 200 );
   ms3.insert( 300 );

   cout << "The original multiset ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the member function version of swap
   ms1.swap( ms2 );

   cout << "After swapping with ms2, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the specialized template version of swap
   swap( ms1, ms3 );

   cout << "After swapping with ms3, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original multiset ms1 is: 10 20 30.
After swapping with ms2, list ms1 is: 100 200.
After swapping with ms3, list ms1 is: 300.
```

## <a name="upper_bound"></a>  multiset::upper_bound

傳回迭代器，指向 multiset 中索引鍵大於指定索引鍵的第一個元素。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>參數

*金鑰*\
要與所搜尋之 multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

**iterator** 或 `const_iterator`，定址對象是 multiset 中索引鍵大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 multiset 中最後一個元素後面的位置。

### <a name="example"></a>範例

```cpp
// multiset_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "The first element of multiset ms1 with a key greater "
           << "than 20 is: " << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key greater than 30." << endl;
   else
      cout << "The element of multiset ms1 with a key > 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.begin( );
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );
   cout << "The first element of ms1 with a key greater than"
        << endl << "that of the initial element of ms1 is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The first element of multiset ms1 with a key greater than 20 is: 30.
The multiset ms1 doesn't have an element with a key greater than 30.
The first element of ms1 with a key greater than
that of the initial element of ms1 is: 20.
```

## <a name="value_comp"></a>  multiset::value_comp

擷取一份用來排序 multiset 中元素值的比較物件複本。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 multiset 用來排序其項目的函式物件，亦即樣板參數 `Compare`。

如需有關 `Compare` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="remarks"></a>備註

預存物件會定義成員函式：

**bool operator**( **const Key&** `_xVal`, **const Key&** `_yVal`);

如果 `_xVal` 在前面且在排序次序中不等於 `_yVal`，此函式就會傳回 true。

請注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 都與範本參數 `Compare` 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

```cpp
// multiset_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of ms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of ms1."
           << endl;
   }

   set <int, greater<int> > ms2;
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.
```

## <a name="value_compare"></a>  multiset::value_compare

一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷它們在 multiset 中的相對順序。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>備註

`value_compare` 與樣板參數 `Compare` 同義。

請注意， [key_compare](#key_compare)和 `value_compare` 都是範本參數 `Compare`的同義字。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

如需有關 `Compare` 的詳細資訊，請參閱 [multiset 類別](../standard-library/multiset-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 [ 的範例，請參閱 ](#value_comp)value_comp`value_compare` 的範例。

## <a name="value_type"></a>  multiset::value_type

一種類型，描述以 multiset 的元素形式儲存且功能為值的物件。

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>備註

`value_type` 與樣板參數 `Key` 同義。

請注意， [key_type](#key_type)和 `value_type` 都是範本參數 `Key`的同義字。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

如需有關 `Key` 的詳細資訊，請參閱該主題的＜備註＞一節。

### <a name="example"></a>範例

```cpp
// multiset_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;

   multiset <int> :: value_type svt_Int;   // Declare value_type
   svt_Int = 10;             // Initialize value_type

   multiset <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   ms1.insert( svt_Int );         // Insert value into s1
   ms1.insert( skt_Int );         // Insert key into s1

   // A multiset accepts key_types or value_types as elements
   cout << "The multiset has elements:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;
}
```

```Output
The multiset has elements: 10 20.
```

## <a name="see-also"></a>另請參閱

[容器](../cpp/containers-modern-cpp.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)
