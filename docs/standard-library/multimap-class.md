---
title: multimap 類別
description: C + + 標準樣板程式庫 (STL) 類別的 API 參考 `multimap` ，用於儲存和抓取集合中的資料，其中每個元素都是具有資料值和排序關鍵字的配對。
ms.date: 9/9/2020
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::contains
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], contains
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: e2d0236a0e643ac92bb771b90a1f021807f03fda
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040674"
---
# <a name="multimap-class"></a>multimap 類別

「C++ 標準程式庫」multimap 類別可用來在集合中儲存及擷取資料，其中集合中的每個元素都成對，同時具有資料值和排序鍵。 索引鍵的值不需要是唯一的，而且會用來自動排序資料。 多重對應中項目的值可以直接變更，但其關聯的索引鍵值不可以直接變更。 相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。

## <a name="syntax"></a>語法

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>參數

*關鍵*\
要存放在多重對應中的索引鍵資料類型。

*類型*\
要存放在多重對應中的項目資料類型。

*性狀*\
類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在多重對應中的相對順序。 二元述詞 `less<Key>` 是預設值。

在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)。

*分配器*\
代表預存配置器物件的類型，封裝有關對應之記憶體配置和解除配置的詳細資訊。 這個引數是選擇性的，而且預設值是 `allocator<pair <const Key, Type> >`。

## <a name="remarks"></a>備註

「C++ 標準程式庫」multimap 類別是：

- 關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。

- 可逆轉的，因為它提供雙向的迭代器以存取其項目。

- 已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。

- 多重，因為它的元素不需要有唯一索引鍵，因此一個索引鍵值可能會有許多相關聯的專案資料值。

- 一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。

- 類別樣板，因為它所提供的功能是泛型，因此獨立于包含做為專案或索引鍵的特定資料類型。 用於項目或索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。

map 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#insert) 和 [multimap](#multimap) 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的一組需求，因此，使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通有關迭代器範圍 `[First, Last)`。

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 關聯的容器已針對查閱、插入和移除作業最佳化。 明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。 插入專案不會使任何反覆運算器無效，移除專案則僅會使已移除元素的反覆運算器失效。

當關聯值與其索引鍵的條件由應用程式滿足時，多重對應應該是首選的關聯容器。 這種結構類型的模型是索引鍵的排序清單，其中包含可提供定義的相關字串值，其中的單字不一定是唯一定義的。 如果關鍵字是唯一定義，因此索引鍵是唯一的，則對應是首選容器。 另一方面，如果只儲存文字清單，則集合是正確的容器。 如果允許多個字組出現，則 `multiset` 會是適當的容器結構。

multimap 會藉由呼叫 [key_compare](#key_compare) 類型的預存函式物件，排序它所控制的序列。 這個預存物件是可藉由呼叫成員函式 [key_comp](#key_comp) 來存取的比較函式。 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 `f(x,y)` 是有兩個引數物件 `x` 和 `y` 以及傳回值 true 或 false 的函式物件。 如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 `x` 和 `y` 在 `f(x,y)` 和 `f(y,x)` 為 false 時定義為相等，則施加於集合的順序是嚴格弱式順序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。

在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱 [關聯容器中的異類查閱](../standard-library/stl-containers.md#sequence_containers) 。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[multimap](#multimap)|建構一個空的 `multimap`，或是其他 `multimap` 的全部或部分複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|類型，表示 `allocator` 物件的 `multimap` 類別。|
|[const_iterator](#const_iterator)|一種類型，提供可讀取中專案的雙向反覆運算器 **`const`** `multimap` 。|
|[const_pointer](#const_pointer)|一種類型，提供 **`const`** 中的元素指標 `multimap` 。|
|[const_reference](#const_reference)|一種類型，提供 **`const`** 儲存在中的元素參考，以 `multimap` 供讀取和執行 **`const`** 作業。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可讀取中任何元素的雙向反覆運算器 **`const`** `multimap` 。|
|[difference_type](#difference_type)|帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中 `multimap` 的項目數。|
|[迭 代](#iterator)|類型，提供兩個參考相同 `multimap` 內項目的迭代器之間的差異。|
|[key_compare](#key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `multimap` 中的相對順序。|
|[key_type](#key_type)|一種類型，描述組成之每個元素的排序關鍵字物件 `multimap` 。|
|[mapped_type](#mapped_type)|類型，表示儲存在 `multimap` 中的資料類型。|
|[指標](#pointer)|一種類型，提供 **`const`** 中的元素指標 `multimap` 。|
|[reference](#reference)|類型，提供儲存在 `multimap` 中之項目的參考。|
|[reverse_iterator](#reverse_iterator)|類型，提供可以讀取或修改反轉 `multimap` 中之項目的雙向迭代器。|
|[size_type](#size_type)|不帶正負號的整數類型，提供 **`const`** 中的元素指標 `multimap` 。|
|[value_type](#value_type)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `multimap` 中的相對順序。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[開始](#begin)|傳回迭代器，為 `multimap` 中的第一個項目定址。|
|[cbegin](#cbegin)|傳回常數迭代器，為 `multimap` 中的第一個項目定址。|
|[cend](#cend)|傳回常數迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|
|[清楚](#clear)|清除 `multimap` 的所有項目。|
|[包含](#contains)<sup>c + + 20</sup>|檢查中是否有具有指定索引鍵的元素 `multimap` 。|
|[計數](#count)|傳回 `multimap` 中索引鍵符合參數指定之索引鍵的項目數目。|
|[crbegin](#crbegin)|傳回常數迭代器，為反轉 `multimap` 中的第一個項目定址。|
|[crend](#crend)|傳回常數迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|
|[emplace](#emplace)|將就地建構的項目插入 `multimap` 中。|
|[emplace_hint](#emplace_hint)|將就地建構的項目 (含位置提示) 插入 `multimap` 中。|
|[empty](#empty)|測試 `multimap` 是否為空白。|
|[結束](#end)|傳回迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|
|[equal_range](#equal_range)|尋找項目索引鍵符合指定值的項目範圍。|
|[erase](#erase)|從指定的位置移除 `multimap` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|
|[find](#find)|傳回迭代器，定址 `multimap` 中索引鍵等於指定索引鍵之項目的第一個位置。|
|[get_allocator](#get_allocator)|傳回用來建構 `allocator` 的 `multimap` 物件複本。|
|[insert](#insert)|將項目或項目範圍插入至 `multimap`。|
|[key_comp](#key_comp)|擷取 `multimap` 中用來排序索引鍵的比較物件之複本。|
|[lower_bound](#lower_bound)|傳回迭代器，指向 `multimap` 中索引鍵等於或大於特定索引鍵的第一個項目。|
|[max_size](#max_size)|傳回 `multimap` 的最大長度。|
|[rbegin](#rbegin)|傳回迭代器，為反轉 `multimap` 中的第一個項目定址。|
|[rend](#rend)|傳回迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|
|[size](#size)|傳回 `multimap` 中項目的數目。|
|[交換](#swap)|交換兩個 `multimap` 的項目。|
|[upper_bound](#upper_bound)|傳回迭代器，指向 `multimap` 中索引鍵大於特定索引鍵的第一個項目。|
|[value_comp](#value_comp)|成員函式傳回函式物件，可藉由比較其索引鍵值判斷 `multimap` 中項目的順序。|

|運算子|描述|
|-|-|
|[運算子 =](#op_eq)|用另一個 `multimap` 的複本取代 `multimap` 的項目。|

## <a name="requirements"></a>需求

**標頭：**\<map>

**命名空間：** std

( **key**, **value**) 配對會以 `pair` 類型的物件形式儲存在 multimap 中。 配對類別需要標頭，此標頭 \<utility> 會自動包含在內 \<map> 。

## <a name="multimapallocator_type"></a><a name="allocator_type"></a> multimap：： allocator_type

一種類型，代表 multimap 物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>範例

如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="multimapbegin"></a><a name="begin"></a> multimap：： begin

傳回迭代器，定址對象是 multimap 中的第一個元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 multimap 中的第一個元素，或空 multimap 後面的位置。

### <a name="example"></a>範例

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="multimapcbegin"></a><a name="cbegin"></a> multimap：： cbegin

傳回 **`const`** 反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**`const`** 雙向存取反覆運算器，指向範圍的第一個元素，或指向空白範圍結尾以外的位置 (空白範圍， `cbegin() == cend()`) 。

### <a name="remarks"></a>備註

如果傳回的值為 `cbegin` ，則無法修改範圍中的元素。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `begin()` `cbegin()` 。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="multimapcend"></a><a name="cend"></a> multimap：： cend

傳回 **`const`** 反覆運算器，定址範圍中最後一個元素之外的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

**`const`** 指向範圍結尾之外的雙向存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `end()` `cend()` 。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

傳回的值不應取值 `cend` 。

## <a name="multimapclear"></a><a name="clear"></a> multimap：： clear

清除 multimap 的所有元素。

```cpp
void clear();
```

### <a name="example"></a>範例

下列範例示範如何使用 multimap::clear 成員函式。

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a> multimap：： const_iterator

一種類型，提供可讀取 multimap 中元素的雙向反覆運算器 **`const`** 。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

型別 `const_iterator` 不能用來修改元素的值。

`const_iterator`由 multimap 所定義的會指向[value_type](#value_type)的物件，這些物件的型別為 `pair<const Key, Type>` 。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。

若要對 `const_iterator` 指向 multimap 中某個元素的 *cIter* 進行取值，請使用 **->** 運算子。

若要存取元素的索引鍵值，請使用 `cIter->first` 相當於的 `(*cIter).first` 。 若要存取專案的對應基準值，請使用 `cIter->second` 相當於的 `(*cIter).second` 。

### <a name="example"></a>範例

如需使用 `const_iterator` 的範例，請參閱 [begin](#begin) 的範例。

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a> multimap：： const_pointer

一種類型，提供 **`const`** multimap 中元素的指標。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

型別 `const_pointer` 不能用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 multimap 物件中的元素。

## <a name="multimapconst_reference"></a><a name="const_reference"></a> multimap：： const_reference

一種類型，提供 **`const`** 儲存在 multimap 中以讀取和執行作業之專案的參考 **`const`** 。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>範例

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> multimap：： const_reverse_iterator

一種類型，提供可讀取 multimap 中任何元素的雙向反覆運算器 **`const`** 。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

型別 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 multimap。

`const_reverse_iterator`由 multimap 所定義的會指向[value_type](#value_type)的物件，這些物件的型別為 `pair<const Key, Type>` 。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。

若要對 `const_reverse_iterator` 指向 multimap 中某個元素的 *crIter* 進行取值，請使用 **->** 運算子。

若要存取元素的索引鍵值，請使用 `crIter->first` 相當於的 `(*crIter).first` 。 若要存取專案的對應基準值，請使用 `crIter->second` 相當於的 `(*crIter).first` 。

### <a name="example"></a>範例

如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#rend) 的範例。

## <a name="multimapcontains"></a><a name="contains"></a> multimap：： contains

檢查中是否有具有指定索引鍵的元素 `multimap` 。

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>參數

*K*\
索引鍵的類型。

*關鍵*\
要尋找之元素的索引鍵值。

### <a name="return-value"></a>傳回值

`true` 如果在容器中找到元素，則為， `false` 否則為。

### <a name="remarks"></a>備註

`contains()` 是 c + + 20 的新功能。 若要使用它，請指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 的編譯器選項。

`template<class K> bool contains(const K& key) const` 如果是透明的，則只會參與多載解析 `key_compare` 。 如需詳細資訊，請參閱 [關聯容器中的異類查閱](https://docs.microsoft.com/cpp/standard-library/stl-containers#heterogeneous-lookup-in-associative-containers-c14) 。

### <a name="example"></a>範例

```cpp
// Requires /std:c++latest
#include <map>
#include <string>
#include <iostream>
#include <functional>

int main()
{
    std::multimap<int, bool> m = {{0, false}, {1, true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << m.contains(1) << '\n';
    std::cout << m.contains(2) << '\n';

    // call template function
    std::multimap<std::string, int, std::less<>> m2 = {{"ten", 10}, {"twenty", 20}, {"thirty", 30}};
    std::cout << m2.contains("ten");
    
    return 0;
}
```

```Output
true
false
true
```

## <a name="multimapcount"></a><a name="count"></a> multimap：： count

傳回 multimap 中索引鍵符合參數指定之索引鍵的項目數。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要從 multimap 中比對之項目的索引鍵。

### <a name="return-value"></a>傳回值

排序索引鍵符合參數索引鍵的項目數。如果 multimap 不含具有相符索引鍵的項目則為 0。

### <a name="remarks"></a>備註

成員函式會傳回範圍中的項目數

\[ lower_bound (*金鑰*) ，upper_bound (*金鑰*) ) 

具有金鑰值索引 *鍵*的。

### <a name="example"></a>範例

下列範例示範如何使用 multimap::count 成員函式。

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements don't need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="multimapcrbegin"></a><a name="crbegin"></a> multimap：： crbegin

傳回常數迭代器，定址對象是反轉 multimap 中的第一個元素。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [multimap](../standard-library/multimap-class.md) 中的第一個元素，或未反轉 `multimap` 中的最後一個元素。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 `multimap` 搭配使用，就如同 [begin](#begin) 是與 `multimap` 搭配使用一樣。

如果傳回的值為 `crbegin` ，則 `multimap` 無法修改物件。

`crbegin` 可用來向後逐一查看 `multimap`。

### <a name="example"></a>範例

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="multimapcrend"></a><a name="crend"></a> multimap：： crend

傳回常數迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [multimap](../standard-library/multimap-class.md) 中最後一個元素後面的位置 (未反轉 `multimap` 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 `multimap` 搭配使用，就如同 [multimap::end](#end) 是與 `multimap` 搭配使用一樣。

如果傳回的值為 `crend` ，則 `multimap` 無法修改物件。

`crend` 可以用來測試反轉迭代器是否已到達其 `multimap` 的結尾。

傳回的值不應取值 `crend` 。

### <a name="example"></a>範例

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="multimapdifference_type"></a><a name="difference_type"></a> multimap：:d ifference_type

一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 multimap 的元素數目。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type`通常用來表示反覆運算器和的範圍 [*first*， *last*) 之間的元素數目，包括指向的專案， `first` `last` `first` 以及最多（但不包括）所指的專案的元素範圍 `last` 。

雖然適用 `difference_type` 于符合輸入反覆運算器需求的所有反覆運算器，其中包括可反轉容器（例如 set）所支援之雙向反覆運算器的類別，但只有隨機存取容器（例如 vector）所提供的隨機存取反覆運算器，才支援反覆運算器之間的減法。

### <a name="example"></a>範例

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="multimapemplace"></a><a name="emplace"></a> multimap：： emplace

插入就地建構 (未執行任何複製或移動作業) 的元素。

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>參數

*參數*\
轉送以建構要插入到 multimap 中之元素的引數。

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

如果在插入時擲回例外狀況，就會將容器保持不變，並重新擲回例外狀況。

元素的 [value_type](../standard-library/map-class.md#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

### <a name="example"></a>範例

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a> multimap：： emplace_hint

將就地建構 (未執行任何複製或移動作業) 的項目連同位置提示一起插入。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>參數

*參數*\
轉送以建構要插入到 multimap 中之元素的引數。

*：*\
要開始搜尋正確的插入點的地方  (如果該點緊接 *在位置*之前，插入可能會在分攤的常數時間（而不是對數時間）發生。 ) 

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

在定位期間，如果擲回例外狀況，就不會修改容器的狀態。

元素的 [value_type](../standard-library/map-class.md#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

如需程式碼範例，請參閱 [map::emplace_hint](../standard-library/map-class.md#emplace_hint)。

## <a name="multimapempty"></a><a name="empty"></a> multimap：： empty

測試 multimap 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 multimap 是空的，則為。 **`false`** 如果 multimap 是空的，則為。

### <a name="example"></a>範例

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="multimapend"></a><a name="end"></a> multimap：： end

傳回超出結尾 (past-the-end) 迭代器。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

超出結尾迭代器。 如果 multimap 是空的，則 `multimap::end() == multimap::begin()`。

### <a name="remarks"></a>備註

**end** 是用來測試迭代器是否已超過其 multimap 的結尾。

**End**傳回的值不應取值。

如需程式碼範例，請參閱 [multimap::find](#find)。

## <a name="multimapequal_range"></a><a name="equal_range"></a> multimap：： equal_range

尋找項目索引鍵符合指定值的項目範圍。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

一組迭代器，其中第一個是索引鍵的 [lower_bound](#lower_bound)，第二個是索引鍵的 [upper_bound](#upper_bound)。

若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **首先** ，若要對下限反覆運算器進行取值，請使用 \* ( `pr` 。 **第一個**) 。 若要存取成員函式所傳回之配對 `pr` 的第二個迭代器，請使用 `pr`. **其次** ，若要取值上限反覆運算器，請使用 \* ( `pr` 。 **第二**) 。

### <a name="example"></a>範例

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="multimaperase"></a><a name="erase"></a> multimap：： erase

從 multimap 中指定的位置移除某個元素或某個範圍的元素，或移除符合指定索引鍵的元素。

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

*：*\
要移除之項目的位置。

*第一*\
要移除之第一個項目的位置。

*最後*\
緊接在要移除之最後一個元素後面的位置。

*關鍵*\
要移除之元素的索引鍵。

### <a name="return-value"></a>傳回值

在前兩個成員函式中，會傳回雙向迭代器，其中指定任何移除的元素之外剩餘的第一個元素，或者如果沒有此類元素，則傳回 map 結尾的元素。

針對第三個成員函式，會傳回已從 multimap 移除的元素數目。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [map::erase](../standard-library/map-class.md#erase)。

## <a name="multimapfind"></a><a name="find"></a> multimap：： find

傳回迭代器，其指向 multimap 中索引鍵等於指定索引鍵的第一個元素的位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要以所搜尋之 multimap 中元素的排序鍵比對的索引鍵值。

### <a name="return-value"></a>傳回值

迭代器，表示具有指定索引鍵的元素位置，或者，如果沒有找到索引鍵的符合項，表示 multimap 中最後一個元素之後的位置 (`multimap::end()`)。

### <a name="remarks"></a>備註

成員函式會傳回迭代器，其表示 multimap 中排序鍵 (在二元述詞下根據較少的比較性關聯引發排序) 等於引數索引鍵的元素。

如果的傳回值 `find` 已指派給 `const_iterator` ，則無法修改 multimap 物件。 如果的傳回值已 `find` 指派給 `iterator` ，則可以修改 multimap 物件。

### <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="multimapget_allocator"></a><a name="get_allocator"></a> multimap：： get_allocator

傳回一份用來建構 multimap 的配置器物件複本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

multimap 所使用的配置器。

### <a name="remarks"></a>備註

multimap 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multimapinsert"></a><a name="insert"></a> multimap：： insert

將某個元素或元素範圍插入 multimap 中。

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

*瓦爾*\
要插入至 multimap 的元素值。

*：*\
要開始搜尋正確的插入點的地方  (如果該點緊接 *在位置*之前，插入可能會在分攤的常數時間（而不是對數時間）發生。 ) 

*ValTy*\
樣板參數，指定對應可以用來建立 [value_type](../standard-library/map-class.md#value_type)之元素的引數類型，並將 *Val* 以引數形式完美轉寄。

*第一*\
要複製之第一個元素的位置。

*最後*\
要複製之最一個元素後方的位置。

*InputIterator*\
符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#value_type) 物件的類型。

*IList*\
要從中複製元素的 [initializer_list](../standard-library/initializer-list.md) 。

### <a name="return-value"></a>傳回值

單一元素插入成員函式 (1) 和 (2)，會將迭代器傳回至在 multimap 中插入新元素的位置。

具有提示的單一元素成員函式 (3) 和 (4)，會傳回迭代器，其指向在 multimap 中插入新元素的位置。

### <a name="remarks"></a>備註

此函式不會使指標或參考無效，但是可能會使容器的所有迭代器無效。

在只插入一個元素的期間，若擲出例外狀況，則不會修改容器的狀態。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。

容器的 [value_type](../standard-library/map-class.md#value_type) 是屬於容器的 typedef，而就 map 而言，`multimap<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

範圍成員函式 (5) 將專案值的序列插入對應至範圍內反覆運算器所定址之每個專案的 multimap 中 `[First, Last)` ，因此，最後不會插入 *最後一個* 元素。 容器成員函式 `end()` 是指容器中最後一個元素後方的位置；例如，陳述式 `m.insert(v.begin(), v.end());` 會將 `v` 的所有元素插入至 `m`。

初始設定式清單成員函式 (6) 會使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 map。

針對插入就地建構 (也就是未執行任何複製或移動作業) 的元素，請參閱 [multimap::emplace](#emplace) 和 [multimap::emplace_hint](#emplace_hint)。

### <a name="example"></a>範例

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="multimapiterator"></a><a name="iterator"></a> multimap：： iterator

一種類型，提供可讀取或修改 multimap 中任何元素的雙向迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

`iterator`由 multimap 所定義的會指向[value_type](#value_type)的物件，這些物件的型別為 `pair<const Key, Type>` 。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。

若要對 `iterator` 指向 multimap 中某個元素的 *Iter* 進行取值，請使用 **->** 運算子。

若要存取元素的索引鍵值，請使用 `Iter->first` 相當於的 `(*Iter).first` 。 若要存取專案的對應基準值，請使用 `Iter->second` 相當於的 `(*Iter).second` 。

類型 `iterator` 可以用來修改元素的值。

### <a name="example"></a>範例

如需如何宣告及使用 `iterator` 的範例，請參閱 [begin](#begin) 的範例。

## <a name="multimapkey_comp"></a><a name="key_comp"></a> multimap：： key_comp

擷取一份用來排序 multimap 中索引鍵的比較物件複本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 multimap 用來排序其元素的函式物件。

### <a name="remarks"></a>備註

預存物件會定義成員函式

`bool operator( const Key& x, const Key& y);`

如果 *x* 在排序次序中絕對位於 *y* 的前面，此函式就會傳回 true。

### <a name="example"></a>範例

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="multimapkey_compare"></a><a name="key_compare"></a> multimap：： key_compare

一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷 multimap 中兩個元素的相對順序。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>備註

`key_compare` 與樣板參數 `Traits` 同義。

如需的詳細資訊 `Traits` ，請參閱 [multimap 類別](../standard-library/multimap-class.md) 主題。

### <a name="example"></a>範例

如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#key_comp) 的範例。

## <a name="multimapkey_type"></a><a name="key_type"></a> multimap：： key_type

一種類型，描述構成 multimap 每個元素的排序鍵物件。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

`key_type` 與樣板參數 `Key` 同義。

如需有關 `Key` 的詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="multimaplower_bound"></a><a name="lower_bound"></a> multimap：： lower_bound

傳回迭代器，指向 multimap 中索引鍵等於或大於指定索引鍵的第一個元素。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

iterator 或 `const_iterator`，定址對象是 multimap 中索引鍵等於或大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 multimap 中最後一個元素後面的位置。

如果的傳回值 `lower_bound` 已指派給 `const_iterator` ，則無法修改 multimap 物件。 如果將 `lower_bound` 的傳回值指派給 **iterator**，則可以修改 multimap 物件。

### <a name="example"></a>範例

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="multimapmapped_type"></a><a name="mapped_type"></a> multimap：： mapped_type

一種類型，代表儲存在 multimap 中的資料類型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>備註

`mapped_type` 與樣板參數 `Type` 同義。

如需的詳細資訊 `Type` ，請參閱 [multimap 類別](../standard-library/multimap-class.md) 主題。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="multimapmax_size"></a><a name="max_size"></a> multimap：： max_size

傳回 multimap 的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

multimap 的最大可能長度。

### <a name="example"></a>範例

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimapmultimap"></a><a name="multimap"></a> multimap：： multimap

建構一個空的 multimap，或是某個其他 multimap 之全部或部分複本的 multimap。

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>參數

*鋁*\
要用於此 multimap 物件的儲存體配置器類別，預設為 Allocator。

*壓縮*\
類型為 `constTraits` 並用來排序 map 中元素的比較函式，預設為 `Traits`。

*對*\
要從中複製所建構之集合的對應。

*第一*\
要複製的元素範圍中第一個元素的位置。

*最後*\
超出要複製之元素範圍的第一個元素的位置。

*IList*\
從中複製項目的 initializer_list。

### <a name="remarks"></a>備註

所有建構函式都會儲存一種配置器物件，此物件可管理 multimap 的記憶體儲存，且之後藉由呼叫 [get_allocator](#get_allocator) 即可傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。

所有建構函式都會將其 multimap 初始化。

所有建構函式都會儲存一個 `Traits` 類型的函式物件，此物件可用來在 multimap 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#key_comp) 即可傳回此物件。

前三個函式會指定空的初始 multimap，第二個是指定比較函式的類型 (要用來建立元素順序的 *複合*) ，而第三個則明確指定要使用的配置器類型 (*Al*) 。 關鍵字會 **`explicit`** 隱藏某些類型的自動類型轉換。

第四個函式會指定 multimap *許可權*的複本。

第五個函式會藉由 *向右*移動來指定 multimap 的複本。

第六、第七及第8個函式會複製 initializer_list 的成員。

接下來的三個建構函式會複製 map 的範圍 `[First, Last)`，其中會以越來越明確的方式指定類別 `Traits` 的比較函式及配置器的類型。

### <a name="example"></a>範例

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="multimapoperator"></a><a name="op_eq"></a> multimap：： operator =

將 multimap 的元素以另一個 multimap 的複本取代。

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>參數

*對*\
要複製到 `multimap` 中的 [multimap](../standard-library/multimap-class.md)。

### <a name="remarks"></a>備註

清除中的任何現有元素之後 `multimap` ，會 `operator=` 將 *右邊* 的內容複寫或移動到 `multimap` 。

### <a name="example"></a>範例

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="multimappointer"></a><a name="pointer"></a> multimap：:p ointer

一種類型，提供 multimap 中元素的指標。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>備註

類型 `pointer` 可以用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 multimap 物件中的元素。

## <a name="multimaprbegin"></a><a name="rbegin"></a> multimap：： rbegin

傳回迭代器，定址對象是反轉 multimap 中的第一個元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 multimap 中的第一個元素，或未反轉 multimap 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 multimap 搭配使用，就如同 [begin](#begin) 是與 multimap 搭配使用一樣。

如果的傳回值 `rbegin` 已指派給，則 `const_reverse_iterator` 無法修改 multimap 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改 multimap 物件。

`rbegin` 可用來向後逐一查看 multimap。

### <a name="example"></a>範例

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="multimapreference"></a><a name="reference"></a> multimap：： reference

一種類型，提供對儲存在 multimap 中元素的參考。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>範例

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="multimaprend"></a><a name="rend"></a> multimap：： rend

傳回迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置 (未反轉 multimap 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 multimap 搭配使用，就如同 [end](../standard-library/map-class.md#end) 是與 multimap 搭配使用一樣。

如果的傳回值 `rend` 已指派給，則 `const_reverse_iterator` 無法修改 multimap 物件。 如果將 `rend` 的傳回值指派給 `reverse_iterator`，則可以修改 multimap 物件。

`rend` 可以用來測試反轉迭代器是否已到達其 multimap 的結尾。

傳回的值不應取值 `rend` 。

### <a name="example"></a>範例

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a> multimap：： reverse_iterator

一種類型，提供可讀取或修改反轉 multimap 中元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 是用來反向逐一查看 multimap。

`reverse_iterator`由 multimap 所定義的會指向[value_type](#value_type)的物件，這些物件的型別為 `pair<const Key, Type>` 。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。

若要對 `reverse_iterator` 指向 multimap 中某個元素的 *rIter* 進行取值，請使用 **->** 運算子。

若要存取元素的索引鍵值，請使用 `rIter->first` 相當於的 `(*rIter).first` 。 若要存取專案的對應基準值，請使用 `rIter->second` 相當於的 `(*rIter).second` 。

### <a name="example"></a>範例

如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#rbegin) 的範例。

## <a name="multimapsize"></a><a name="size"></a> multimap：： size

傳回 multimap 中的項目數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

multimap 的目前長度。

### <a name="example"></a>範例

下列範例示範如何使用 multimap::size 成員函式。

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="multimapsize_type"></a><a name="size_type"></a> multimap：： size_type

一種不帶正負號的整數類型，可計算 multimap 中的元素數目。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例。

## <a name="multimapswap"></a><a name="swap"></a> multimap：： swap

交換兩個 multimap 的元素。

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
提供要交換之元素的 multimap，或要與 multimap `left` 交換元素的 multimap。

### <a name="remarks"></a>備註

任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 multimap 中，成員函式就不會使其失效。

### <a name="example"></a>範例

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="multimapupper_bound"></a><a name="upper_bound"></a> multimap：： upper_bound

傳回迭代器，指向 multimap 中索引鍵大於指定索引鍵的第一個元素。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

iterator 或 `const_iterator`，定址對象是 multimap 中索引鍵大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 multimap 中最後一個元素後面的位置。

如果傳回值已指派給 `const_iterator` ，則無法修改 multimap 物件。 如果將傳回值指派給 `iterator` ，則可以修改 multimap 物件。

### <a name="example"></a>範例

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="multimapvalue_comp"></a><a name="value_comp"></a> multimap：： value_comp

成員函式會傳回函式物件，此物件可藉由比較 multimap 中元素的索引鍵值來判斷這些元素的順序。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 multimap 用來排序其元素的比較函式物件。

### <a name="remarks"></a>備註

針對 multimap *m*，如果有兩個元素 *e1* (*版 k1*、 *d1*) 和 *e2* (*k2*， *D2*) 是類型的物件 `value_type` ，其中 *版 k1* 和 *k2* 是其類型的索引鍵，而 `key_type` *d1* 和 *D2* 是其類型的資料 `mapped_type` ，則 `m.value_comp(e1, e2)` 相當於 `m.key_comp(k1, k2)` 。

### <a name="example"></a>範例

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="multimapvalue_type"></a><a name="value_type"></a> multimap：： value_type

一種類型，代表以元素形式儲存在 map 中的物件類型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>範例

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>另請參閱

[容器](../cpp/containers-modern-cpp.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
