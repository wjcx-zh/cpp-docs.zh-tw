---
title: hash_multiset 類別
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 984e53a4662b8e3bc18cf06f9fc71d5a614b86ea
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448691"
---
# <a name="hashmultiset-class"></a>hash_multiset 類別

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

容器類別 hash_multiset 是「C++ 標準程式庫」的擴充功能，可用來在集合中儲存及快速擷取資料，其中集合中所含的元素值會作為索引鍵值且不一定要是唯一的。

## <a name="syntax"></a>語法

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>參數

*擊鍵*\
要存放在 hash_multiset 中的項目資料類型。

*共同*\
包含兩個函式物件的類型, 其中一個是二元述詞, 可將兩個專案值做為排序關鍵字進行比較, 以判斷其相對順序和雜湊函式, 其為專案的一元述詞對應索引鍵值為不帶正負號類型`size_t`的整數。 這個引數是選用引數，且預設值是 `hash_compare<Key, less<Key> >`。

*配置器*\
代表預存配置器物件的類型，封裝有關 hash_multiset 之記憶體配置和解除配置的詳細資訊。 這個引數是選用引數，且預設值是 `allocator<Key>`。

## <a name="remarks"></a>備註

hash_multiset 是：

- 關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。 此外，它是簡單關聯的容器，因為其項目值是其索引鍵值的。

- 可逆轉的，因為它提供雙向的迭代器以存取其項目。

- 已經過雜湊處理，因為其項目會依據套用至該項目索引鍵值之雜湊函式的值，分組到不同值區。

- 唯一，因為它的每個項目都必須具有唯一索引鍵。 因為 hash_multiset 也是簡式的相關聯容器，所以其項目也不會重複。

- 範本類別，因為它提供的功能是泛型，因此與作為項目或索引鍵包含的特定資料類型是獨立的。 用於項目或索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。

透過排序進行雜湊的主要優點是效率更佳：成功的雜湊能執行插入、刪除，相較於和排序技術容器中項目數目對數值成比例的時間，它會以常數平均時間進行搜尋。 集合中項目的索引鍵值不能直接變更。 相反地，必須刪除舊值，並插入具有新值的項目。

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 經過雜湊處理的相關聯容器，已針對查閱、插入及移除作業進行過最佳化。 搭配設計良好的雜湊函式使用時，明確支援這些作業的成員函式，效率相當良好，其會以平均而言為常數的時間執行作業，而與此容器中的項目數目無關。 設計良好的雜湊函式會產生雜湊值的均勻分佈，並盡可能減少衝突發生，當相異索引鍵值對應到相同的雜湊值時，就會發生所謂的衝突。 使用最糟的雜湊函式的最壞情況下，作業數目與序列中的項目數目成正比 (線性時間)。

當關聯值與其索引鍵的條件由應用程式滿足時，hash_multiset 應該是首選的關聯容器。 hash_multiset 的項目可以是多重，並當做自己的排序鍵，因此索引鍵不是唯一的。 例如，這種結構的模型是文字的已排序清單，其中文字可以出現多次。 如果不允許文字的多個項目，則 hash_set 是適當的容器結構。 如果唯一定義做為值附加至唯一關鍵字清單，則 hash_map 是包含這個資料的適當結構。 如果定義不是唯一的，則 hash_multimap 是首選容器。

hash_multiset 會藉由呼叫 [value_compare](#value_compare) 類型的預存雜湊特性物件，排序它所控制的序列。 藉由呼叫成員函式 [key_comp](#key_comp)，即可存取這個預存物件。 這類函式物件的行為必須與類別`hash_compare<Key, less<Key> >`的物件相同。 具體而言, 針對類型 `Key`的所有值索引鍵, `Trait(Key)`呼叫會產生類型`size_t`值的分佈。

通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 *f*( *x*, *y*) 是有兩個引數物件 x 和 y 以及傳回值 true 或 false 的函式物件。 如果二元述詞是非自反、反對稱性且可轉移的，而且如果等價是可轉移的，其中兩個物件 x 和 y 是定義為當 *f*( *x*, *y*) 和 *f*( *y*, *x*) 皆為 false 時即相等，則施加於 hash_multiset 的排序是嚴格弱式排序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。

受控制序列中實際的項目順序取決於雜湊函式、排序函式以及儲存於此容器物件中雜湊資料表目前的大小。 您無法判斷目前雜湊資料表的大小，因此一般而言，無法預測受控制序列中項目的順序。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。

hash_multiset 類別提供的迭代器是雙向迭代器，但類別成員函式 insert 和 hash_multiset 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的 hash_multiset 需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是最基本的功能 hash_multiset，但已足以在類別成員函式的內容中，有意義地溝通迭代器 [ `first`, `last`) 的範圍。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[hash_multiset](#hash_multiset)|建構一個空的 `hash_multiset`，或是其他 `hash_multiset` 的全部或部分複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[allocator_type](#allocator_type)|類型，表示 `allocator` 物件的 `hash_multiset` 類別。|
|[const_iterator](#const_iterator)|一種類型, 提供可讀取中`hash_multiset` **const**元素的雙向反覆運算器。|
|[const_pointer](#const_pointer)|一種類型, 提供中`hash_multiset` **const**元素的指標。|
|[const_reference](#const_reference)|一種類型, 提供儲存在中 `hash_multiset`以供讀取和執行**const**運算之 const 元素的參考。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型, 提供可讀取中`hash_multiset`任何**const**元素的雙向反覆運算器。|
|[difference_type](#difference_type)|提供為相同 `hash_multiset` 中項目定址之兩個迭代器間差異的帶正負號的整數類型。|
|[iterator](#iterator)|類型，其提供可讀取或修改 `hash_multiset` 中任何項目的雙向迭代器。|
|[key_compare](#key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `hash_multiset` 中的相對順序。|
|[key_type](#key_type)|類型，其描述在做為排序鍵的功能上，儲存為 `hash_set` 項目的物件。|
|[pointer](#pointer)|類型，其提供 `hash_multiset` 中項目的指標。|
|[reference](#reference)|類型，提供儲存在 `hash_multiset` 中之項目的參考。|
|[reverse_iterator](#reverse_iterator)|類型，提供可以讀取或修改反轉 `hash_multiset` 中之項目的雙向迭代器。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `hash_multiset` 中的項目數。|
|[value_compare](#value_compare)|類型，其提供兩個函式物件，一個是可以比較 `hash_multiset` 兩個項目值的 compare 類別以決定其相對順序的二元述詞，以及會將項目進行雜湊處理的一元述詞。|
|[value_type](#value_type)|類型，其描述在做為值的功能上，儲存為 `hash_multiset` 項目的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[begin](#begin)|傳回迭代器，會定址到`hash_multiset` 中的第一個項目。|
|[cbegin](#cbegin)|傳回常數迭代器，為 `hash_multiset` 中的第一個項目定址。|
|[cend](#cend)|傳回常數迭代器，為 `hash_multiset` 中最後一個項目的下一個位置定址。|
|[clear](#clear)|清除 `hash_multiset` 的所有項目。|
|[計數](#count)|傳回 `hash_multiset` 中索引鍵符合參數指定之索引鍵的項目數目。|
|[crbegin](#crbegin)|傳回常數迭代器，為反轉 `hash_multiset` 中的第一個項目定址。|
|[crend](#crend)|傳回常數迭代器，為反轉 `hash_multiset` 中最後一個項目的下一個位置定址。|
|[emplace](#emplace)|將就地建構的項目插入 `hash_multiset` 中。|
|[emplace_hint](#emplace_hint)|將就地建構的項目 (含位置提示) 插入 `hash_multiset` 中。|
|[empty](#empty)|測試 `hash_multiset` 是否為空白。|
|[end](#end)|傳回迭代器，為 `hash_multiset` 中最後一個項目的下一個位置定址。|
|[equal_range](#equal_range)|傳回成對的迭代器，分別指向 `hash_multiset` 中索引鍵大於特定索引鍵的第一個項目，以及指向 `hash_multiset` 中索引鍵等於或大於該索引鍵的第一個項目。|
|[erase](#erase)|從指定的位置移除 `hash_multiset` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|
|[find](#find)|傳回迭代器，為 `hash_multiset` 中索引鍵等於指定索引鍵項目位置定址。|
|[get_allocator](#get_allocator)|傳回用來建構 `allocator` 的 `hash_multiset` 物件複本。|
|[insert](#insert)|將項目或項目範圍插入至 `hash_multiset`。|
|[key_comp](#key_compare)|擷取 `hash_multiset` 中用來排序索引鍵的比較物件之複本。|
|[lower_bound](#lower_bound)|傳回迭代器，指向 `hash_multiset` 中索引鍵等於或大於特定索引鍵的第一個項目。|
|[max_size](#max_size)|傳回 `hash_multiset` 的最大長度。|
|[rbegin](#rbegin)|傳回迭代器，為反轉 `hash_multiset` 中的第一個項目定址。|
|[rend](#rend)|傳回迭代器，為反轉 `hash_multiset` 中最後一個項目的下一個位置定址。|
|[size](#size)|傳回 `hash_multiset` 中項目的數目。|
|[swap](#swap)|交換兩個 `hash_multiset` 的項目。|
|[upper_bound](#upper_bound)|傳回迭代器，指向 `hash_multiset` 中索引鍵等於或大於特定索引鍵的第一個項目。|
|[value_comp](#value_comp)|擷取一份用以進行雜湊及排序 `hash_multiset` 中項目索引鍵值的雜湊特性物件複本。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[hash_multiset::operator=](#op_eq)|將 hash_multiset 的元素以另一個 hash_multiset 的複本取代。|

## <a name="requirements"></a>需求

**標頭：** \<hash_set>

**命名空間：** stdext

## <a name="allocator_type"></a>  hash_multiset::allocator_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，代表 hash_multiset 物件的配置器類別。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>範例

如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#get_allocator) 的範例

## <a name="begin"></a>  hash_multiset::begin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，定址對象是 hash_multiset 中的第一個元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 hash_multiset 中的第一個元素，或空 hash_multiset 後面的位置。

### <a name="remarks"></a>備註

如果將的傳回值`begin`指派`const_iterator`給, 則無法修改 hash_multiset 物件中的元素。 如果將的傳回值`begin`指派`iterator`給, 則可以修改 hash_multiset 物件中的元素。

### <a name="example"></a>範例

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>  hash_multiset::cbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回常數迭代器，定址對象是 hash_multiset 中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

常數雙向迭代器，定址對象是 [hash_multiset](../standard-library/hash-multiset-class.md) 中的第一個元素，或空 `hash_multiset` 後面的位置。

### <a name="remarks"></a>備註

有 `cbegin` 的傳回值時，無法修改 `hash_multiset` 物件中的元素。

### <a name="example"></a>範例

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>  hash_multiset::cend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回常數迭代器，定址對象是 hash_multiset 中最後一個元素後面的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

常數雙向迭代器，定址對象是 [hash_multiset](../standard-library/hash-multiset-class.md) 中最後一個元素後面的位置。 如果 `hash_multiset` 是空的，則 `hash_multiset::cend == hash_multiset::begin`。

### <a name="remarks"></a>備註

`cend` 是用來測試迭代器是否已到達其 `hash_multiset` 的結尾。 `cend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>  hash_multiset::clear

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

清除 hash_multiset 的所有元素。

```cpp
void clear();
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multiset::const_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供可讀取 hash_multiset 中 **const** 元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

### <a name="example"></a>範例

如需使用 `const_iterator` 的範例，請參閱 [begin](#begin) 的範例。

## <a name="const_pointer"></a>  hash_multiset::const_pointer

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供 hash_multiset 中 **const** 元素的指標。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。

在大多數情況下，應該使用 [const_iterator](#const_iterator) 來存取 **const** hash_multiset 物件中的元素。

## <a name="const_reference"></a>  hash_multiset::const_reference

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供對儲存在 hash_multiset 中以供讀取和執行 **const** 運算之 **const** 元素的參考。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供可讀取 hash_multiset 中任何 **const** 元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 hash_multiset。

### <a name="example"></a>範例

如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#rend) 的範例。

## <a name="count"></a>  hash_multiset::count

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回 hash_multiset 中索引鍵符合參數指定之索引鍵的項目數。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要從 hash_multiset 中比對之項目的索引鍵。

### <a name="return-value"></a>傳回值

hash_multiset 中具有參數指定之索引鍵的項目數。

### <a name="remarks"></a>備註

成員函式會傳回下列範圍中的項目數：

\[lower_bound (*key*)、upper_bound (*key*))。

### <a name="example"></a>範例

下列範例示範如何使用 hash_multiset::count 成員函式。

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_multiset::crbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回常數迭代器，定址對象是反轉 hash_multiset 中的第一個元素。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [hash_multiset](../standard-library/hash-multiset-class.md) 中的第一個元素，或未反轉 `hash_multiset` 中的最後一個元素。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 `hash_multiset` 搭配使用，就如同 [hash_multiset::begin](#begin) 是與 `hash_multiset` 搭配使用一樣。

有 `crbegin` 的傳回值時，無法修改 `hash_multiset` 物件。

`crbegin` 可用來向後逐一查看 `hash_multiset`。

### <a name="example"></a>範例

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>  hash_multiset::crend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回常數迭代器，定址對象是反轉 hash_multiset 中最後一個元素後面的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [hash_multiset](../standard-library/hash-multiset-class.md) 中最後一個元素後面的位置 (未反轉 `hash_multiset` 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 `hash_multiset` 搭配使用，就如同 [hash_multiset::end](#end) 是與 `hash_multiset` 搭配使用一樣。

有 `crend` 的傳回值時，無法修改 `hash_multiset` 物件。

`crend` 可以用來測試反轉迭代器是否已到達其 hash_multiset 的結尾。

### <a name="example"></a>範例

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>  hash_multiset::difference_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種帶正負號的整數類型，提供定址對象為相同 hash_multiset 中元素之兩個迭代器間的差異。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 `first` 和 `last` 之間範圍 [ `first`, `last`) 內的元素數目，包括 `first` 所指的元素以及上限到 `last` 所指元素 (但不包含此元素) 的元素範圍。

請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別， 但只有隨機存取容器 (例如 vector 或 deque) 所提供的隨機存取迭代器，才支援迭代器之間的減法。

### <a name="example"></a>範例

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>  hash_multiset::emplace

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

將就地建構的元素插入到 hash_multiset 中。

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*val*|要插入到 [hash_multiset](../standard-library/hash-multiset-class.md) 中之元素的值，除非 `hash_multiset` 已經包含該元素，或更廣泛地說，即索引鍵以同等方式排序的元素。|

### <a name="return-value"></a>傳回值

`emplace` 成員函式會傳回迭代器，此迭代器指向新元素的插入位置。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>  hash_multiset::emplace_hint

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

將就地建構的元素 (含位置提示) 插入到 hash_multiset 中。

```cpp
template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>參數

|參數|說明|
|-|-|
|*val*|要插入到 [hash_multiset](../standard-library/hash-multiset-class.md) 中之元素的值，除非 `hash_multiset` 已經包含該元素，或更廣泛地說，即索引鍵以同等方式排序的元素。|
|*_Where*|要開始搜尋正確的插入點的地方。 (如果插入點緊接在 *_Where*後面, 則會在分攤的常數時間中進行插入, 而不是對數時間)。|

### <a name="return-value"></a>傳回值

[hash_multiset::emplace](#emplace) 成員函式會傳回迭代器，此迭代器指向新元素在 `hash_multiset` 中的插入位置。

### <a name="remarks"></a>備註

如果插入點緊接在 *_Where*之後, 則會在分攤的常數時間 (而不是對數時間) 中進行插入。

### <a name="example"></a>範例

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>  hash_multiset::empty

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

測試 hash_multiset 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果 hash_multiset 是空的，即為 **true**；如果 hash_multiset 不是空的，則為 **false**。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>  hash_multiset::end

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，定址對象是 hash_multiset 中最後一個元素後面的位置。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 hash_multiset 中最後一個元素後面的位置。 如果 hash_multiset 是空的，則 hash_multiset::end == hash_multiset::begin。

### <a name="remarks"></a>備註

`end`是用來測試反覆運算器是否已到達其 hash_multiset 的結尾。 `end` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>  hash_multiset::equal_range

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回一組迭代器，分別指向 hash_multiset 中索引鍵大於指定索引鍵的第一個元素，以及指向 hash_multiset 中索引鍵等於或大於該索引鍵的第一個元素。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之 hash_multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

一對迭代器，其中第一個是索引鍵的 [lower_bound](#lower_bound)，第二個則是索引鍵的 [upper_bound](#upper_bound)。

若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之配對 `pr` 的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。

### <a name="example"></a>範例

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_multiset::erase

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

從指定的位置移除 hash_multiset 中的項目或項目範圍，或移除符合指定索引鍵的項目。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>參數

*_Where*\
要從 hash_multiset 移除項目的位置。

*頭*\
從 hash_multiset 移除第一個項目的位置。

*次*\
從 hash_multiset 移除最後一個項目之外的位置。

*擊鍵*\
要從 hash_multiset 中移除之項目的索引鍵。

### <a name="return-value"></a>傳回值

若為前兩個成員函式，會移除任何項目之外指定第一個剩餘項目的雙向迭代器，或如果沒有這類項目存在，則為 hash_multiset 結尾的指標。 若為第三個成員函式，已經從 hash_multiset 移除的項目數。

### <a name="remarks"></a>備註

成員函式永遠不會擲回例外狀況。

### <a name="example"></a>範例

下列範例示範使用 hash_multiset:: erase 成員函式。

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>  hash_multiset::find

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，定址對象是 hash_multiset 中索引鍵等於指定索引鍵的元素位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要以所搜尋之 hash_multiset 中元素的排序鍵比對的引數索引鍵。

### <a name="return-value"></a>傳回值

[iterator](#iterator) 或 [const_iterator](#const_iterator)，定址對象是等於指定索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_multiset 中最後一個元素後面的位置。

### <a name="remarks"></a>備註

此成員函式會傳回反覆運算器, 其定址 hash_multiset 中的專案, 其`equivalent`排序關鍵字是在根據小於可比較性關聯而引發排序的二元述詞下的引數索引鍵。

如果將的傳回值`find`指派`const_iterator`給, 則無法修改 hash_multiset 物件。 如果將的傳回值`find`指派`iterator`給, 則可以修改 hash_multiset 物件。

### <a name="example"></a>範例

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_multiset::get_allocator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回一份用來建構 hash_multiset 的配置器物件複本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>傳回值

hash_multiset 用來管理記憶體的配置器，亦即此類別的範本參數 `Allocator`。

如需有關 `Allocator` 的詳細資訊，請參閱 [hash_multiset 類別](../standard-library/hash-multiset-class.md)主題的＜備註＞一節。

### <a name="remarks"></a>備註

hash_multiset 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器，足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
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

## <a name="hash_multiset"></a>  hash_multiset::hash_multiset

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

建構一個空的 `hash_multiset`，或是其他 `hash_multiset` 的全部或部分複本。

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>參數

|參數|說明|
|-|-|
|*Al*|要用於此 `hash_multiset` 物件的儲存體配置器類別，預設為 `Allocator`。|
|*背光*|類型為 `const Traits` 並用來排序 `hash_multiset` 中元素的比較函式，預設為 `hash_compare`。|
|*右邊*|要從中複製所建構之 `hash_multiset` 的 `hash_multiset`。|
|*頭*|要複製的元素範圍中第一個元素的位置。|
|*次*|超出要複製之元素範圍的第一個元素的位置。|
|*IList*|包含要複製之項目的 initializer_list。|

### <a name="remarks"></a>備註

所有建構函式都會儲存一種配置器物件，此物件可管理 `hash_multiset` 的記憶體儲存，且之後藉由呼叫 [hash_multiset::get_allocator](#get_allocator) 即可傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。

所有建構函式都會將其 hash_multiset 初始化。

所有建構函式都會儲存一個 `Traits` 類型的函式物件，此物件可用來在 `hash_multiset` 的索引鍵之間建立順序，且之後藉由呼叫 [hash_multiset::key_comp](#key_comp) 即可傳回此物件。 如需有關 `Traits` 的詳細資訊，請參閱 [hash_multiset 類別](../standard-library/hash-multiset-class.md)主題。

前三個函式會指定空`hash_multiset`的初始, 第二個是指定要用來建立元素順序的比較函數 (*Comp*) 類型, 而第三個是明確指定配置器類型 (*Al*)要使用的。 關鍵字 **explicit** 會隱藏某些類型的自動類型轉換。

第四個函數會`hash_multiset`移動`Right`。

第五、第六及第七個建構函式會使用 initializer_list。

最後三個建構函式會複製 `hash_multiset` 的範圍 [ `First`, `Last`)，其中會以越來越明確的方式指定類別 Compare 的比較函式及配置器的類型。

雜湊集合容器中元素的實際順序取決於雜湊函式、排序函式及雜湊表目前的大小，而通常無法像僅由排序函式決定的 set 容器一樣可供預測。

## <a name="insert"></a>  hash_multiset::insert

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

將某個元素或某個範圍的元素插入到 hash_multiset。

```cpp
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,
    const Type& Val);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*初始值*|要插入到 hash_multiset 中之元素的值，除非 hash_multiset 已經包含該元素，或更廣泛地說，即索引鍵以同等方式排序的元素。|
|*Where*|要開始搜尋正確的插入點的地方。 (如果插入點緊接在 `_Where` 之後，便可以分攤的常數時間 (而不是對數時間) 進行插入)。|
|*頭*|要從 hash_multiset 複製之第一個元素的位置。|
|*次*|緊接在要從 hash_multiset 複製之最後一個元素後面的位置。|
|*IList*|包含要複製之元素的 initializer_list。|

### <a name="return-value"></a>傳回值

前兩個 insert 成員函式會傳回迭代器，此迭代器指向新元素的插入位置。

接下來的三個成員函式會使用 initializer_list。

第三個成員函式會將元素值的序列插入到與每個元素對應的 hash_multiset 中，而這些元素是由指定 hash_multiset 之範圍 [ `First`, `Last`) 中的迭代器所定址。

### <a name="remarks"></a>備註

插入的提示版本可能會在分攤的常數時間內進行插入, 而不是對數時間, 如果插入點緊接在*Where*的後面。

## <a name="iterator"></a>  hash_multiset::iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供可讀取或修改 hash_multiset 中任何元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>備註

類型`iterator`可用於修改元素的值。

### <a name="example"></a>範例

如需如何[](#begin)宣告和使用`iterator`的範例, 請參閱 begin 的範例。

## <a name="key_comp"></a>  hash_multiset::key_comp

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

擷取一份用來排序 hash_multiset 中索引鍵的比較物件複本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 hash_multiset 範本參數*特性*, 其中包含用來雜湊處理及排序容器元素的函式物件。

如需有關*特性*的詳細資訊, 請參閱[hash_multiset 類別](../standard-library/hash-multiset-class.md)主題。

### <a name="remarks"></a>備註

預存物件會定義成員函式：

**bool operator**( **const Key&** *_xVal,* **const Key&** _ `yVal`);

如果 `_xVal` 在前面且在排序次序中不等於 `_yVal`，此函式就會傳回 **true**。

請注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 都與樣板參數 *Traits* 同義。 針對 hash_set 和 hash_multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 hash_map 和 hash_multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multiset::key_compare

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種提供兩個函式物件的類型：一個是可比較 hash_multiset 的兩個元素值以判斷其相對順序的 compare 類別二元述詞，一個是將元素雜湊處理的一元述詞。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>備註

`key_compare`是範本參數*特性*的同義字。

如需有關*特性*的詳細資訊, 請參閱[hash_multiset 類別](../standard-library/hash-multiset-class.md)主題。

請注意，`key_compare` 和 value_compare 都與範本參數 *Traits* 同義。 針對 hash_set 和 hash_multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 hash_map 和 hash_multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#key_comp) 的範例。

## <a name="key_type"></a>  hash_multiset::key_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種提供函式物件的類型，該函式物件可比較排序鍵來判斷 hash_multiset 中兩個元素的相對順序。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

`key_type`是範本參數索引*鍵*的同義字。

請注意，`key_type` 和 [value_type](../standard-library/hash-set-class.md#value_type) 都與樣板參數 *Key* 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

如需*金鑰*的詳細資訊, 請參閱[hash_multiset 類別](../standard-library/hash-multiset-class.md)主題的「備註」一節。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="lower_bound"></a>  hash_multiset::lower_bound

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，指向 hash_multiset 中索引鍵等於或大於指定索引鍵的第一個元素。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之 hash_multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

[iterator](#iterator) 或 [const_iterator](#const_iterator)，定址對象是 hash_multiset 中索引鍵等於或大於引數索引鍵的第一個元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_multiset 中最後一個元素後面的位置。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>  hash_multiset::max_size

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回 hash_multiset 的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

hash_multiset 的最大可能長度。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multiset::operator=

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

將 hash_multiset 的元素以另一個 hash_multiset 的複本取代。

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>參數

|參數|說明|
|-|-|
|*right*|要複製到 `hash_multiset` 中的 [hash_multiset](../standard-library/hash-multiset-class.md)。|

### <a name="remarks"></a>備註

清除中的任何現有專案之後`hash_multiset`, `operator=`會將的`hash_multiset`內容複寫或移到中。

### <a name="example"></a>範例

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_multiset::pointer

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供 hash_multiset 中元素的指標。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>備註

類型`pointer`可用於修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 multiset 物件中的元素。

## <a name="rbegin"></a>  hash_multiset::rbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，定址對象是反轉 hash_multiset 中的第一個元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 hash_multiset 中的第一個元素，或未反轉 hash_multiset 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 hash_multiset 搭配使用，就如同 [begin](#begin) 是與 hash_multiset 搭配使用一樣。

如果將 `rbegin` 的傳回值指派給 `const_reverse_iterator`，便無法修改 hash_multiset 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改 hash_multiset 物件。

`rbegin` 可用來向後逐一查看 hash_multiset。

### <a name="example"></a>範例

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>  hash_multiset::reference

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供對儲存在 hash_multiset 中元素的參考。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>  hash_multiset::rend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，定址對象是反轉 hash_multiset 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 hash_multiset 中最後一個元素後面的位置 (未反轉 hash_multiset 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 hash_multiset 搭配使用，就如同 [end](#end) 是與 hash_multiset 搭配使用一樣。

如果將 `rend` 的傳回值指派給 `const_reverse_iterator`，便無法修改 hash_multiset 物件。 如果將 `rend` 的傳回值指派給 `reverse_iterator`，則可以修改 hash_multiset 物件。 `rend` 所傳回的值不應該取值。

`rend` 可以用來測試反轉迭代器是否已到達其 hash_multiset 的結尾。

### <a name="example"></a>範例

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，提供可讀取或修改反轉 hash_multiset 中元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 是用來反向逐一查看 hash_multiset。

### <a name="example"></a>範例

如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#rbegin) 的範例。

## <a name="size"></a>  hash_multiset::size

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回 hash_multiset 中的元素數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

hash_multiset 的目前長度。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>  hash_multiset::size_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種不帶正負號的整數類型，可代表 hash_multiset 中的元素數目。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例

## <a name="swap"></a>  hash_multiset::swap

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

交換兩個 hash_multiset 的元素。

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>參數

*再*\
提供要與目標 hash_multiset 交換之元素的引數 hash_multiset。

### <a name="remarks"></a>備註

任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 hash_multiset 中，成員函式就不會使其失效。

### <a name="example"></a>範例

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>  hash_multiset::upper_bound

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

傳回迭代器，指向 hash_multiset 中索引鍵大於指定索引鍵的第一個元素。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之 hash_multiset 中元素的排序鍵比較的引數索引鍵。

### <a name="return-value"></a>傳回值

[iterator](#iterator) 或 [const_iterator](#const_iterator)，定址對象是 hash_multiset 中索引鍵大於引數索引鍵的第一個元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_multiset 中最後一個元素後面的位置。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>  hash_multiset::value_comp

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

擷取一份用來排序 hash_multiset 中元素值的比較物件複本。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 hash_multiset 範本參數*特性*, 其中包含用來雜湊處理及排序容器元素的函式物件。

如需有關*特性*的詳細資訊, 請參閱[hash_multiset 類別](../standard-library/hash-multiset-class.md)主題。

### <a name="remarks"></a>備註

預存物件會定義成員函式：

**bool operator**( **constKey&** `_xVal`, **const Key&** *_yVal*);

如果 `_xVal` 在前面且在排序次序中不等於 `_yVal`，此函式就會傳回 **true**。

請注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 都與樣板參數 *Traits* 同義。 針對 hash_set 和 hash_multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 hash_map 和 hash_multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>  hash_multiset::value_compare

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種提供兩個函式物件的類型：一個是可比較 hash_multiset 的兩個元素值以判斷其相對順序的 compare 類別二元述詞，一個是將元素雜湊處理的一元述詞。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>備註

`value_compare`是範本參數*特性*的同義字。

如需有關*特性*的詳細資訊, 請參閱[hash_multiset 類別](../standard-library/hash-multiset-class.md)主題。

請注意, [key_compare](#key_compare)和`value_compare`都是範本參數*特性*的同義字。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。

### <a name="example"></a>範例

如需如何宣告及使用 `value_compare` 的範例，請參閱 [value_comp](#value_comp) 的範例。

## <a name="value_type"></a>  hash_multiset::value_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

一種類型，描述以 hash_multiset 的元素形式儲存且功能為值的物件。

```cpp
typedef Key value_type;
```

### <a name="example"></a>範例

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
