---
title: hash_map 類別
ms.date: 11/04/2016
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
ms.openlocfilehash: 67f891ae7e0b9eab10b1cceda8736661a24641bb
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560645"
---
# <a name="hash_map-class"></a>hash_map 類別

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

從集合中快速儲存和擷取資料，其中每個項目為具有已排序索引鍵 (其值唯一) 和相關聯資料值的配對。

## <a name="syntax"></a>語法

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>參數

*關鍵*\
要存放在 hash_map 中的索引鍵資料類型。

*類型*\
要存放在 hash_map 中的項目資料類型。

*性狀*\
包含兩個函式物件的類型：一個 compare 類別可以將兩個項目值做為排序索引鍵加以比較，以決定其相對順序；一個雜湊函式，為項目的一元述詞對應索引鍵值，對應到 `size_t` 類型之不帶正負號的整數。 這個引數是選擇性的，且 hash_compare<`Key` ，較不<`Key`> > 是預設值。

*分配器*\
代表預存配置器物件的類型，封裝有關 hash_map 之記憶體配置和解除配置的詳細資訊。 這個引數是選擇性的，預設值是配置器 \<pair <const `Key`, `Type`>>。

## <a name="remarks"></a>備註

此 hash_map 是：

- 關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。

- 可逆轉的，因為它提供雙向的迭代器以存取其項目。

- 已經過雜湊處理，因為其項目會依據套用至該項目索引鍵值之雜湊函式的值，分組到不同值區。

- 唯一，因為它的每個項目都必須具有唯一索引鍵。

- 一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。

- 類別樣板，因為它所提供的功能是泛型，因此獨立于包含做為專案或索引鍵的特定資料類型。 用於項目或索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。

透過排序進行雜湊的主要優點是效率更佳；成功的雜湊能執行插入、刪除，相較於和排序技術容器中項目數目對數值成比例的時間，它會以常數平均時間進行搜尋。 Hash_map 中項目的值可以直接變更，但其關聯的索引鍵值不可以直接變更。 相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 經過雜湊處理的相關聯容器，已針對查閱、插入及移除作業進行過最佳化。 搭配設計良好的雜湊函式使用時，明確支援這些作業的成員函式，效率相當良好，其會以平均而言為常數的時間執行作業，而與此容器中的項目數目無關。 設計良好的雜湊函式會產生雜湊值的均勻分佈，並盡可能減少衝突發生，當相異索引鍵值對應到相同的雜湊值時，就會發生所謂的衝突。 使用最糟的雜湊函式的最壞情況下，作業數目與序列中的項目數目成正比 (線性時間)。

當關聯值與其索引鍵的條件由應用程式滿足時，hash_map 應該要當成首選的關聯容器。 這個類型結構的模型是已排序的唯一關鍵字清單，舉例而言，其中關聯的字串值可提供定義。 相反地，如果文字具有一個以上的正確定義，並且索引鍵不是唯一的，則 hash_multimap 是首選容器。 另一方面，如果只儲存了文字清單，則 hash_set 會是正確的容器。 如果允許出現多次文字，則 hash_multiset 即是適當的容器結構。

Hash_map 藉由呼叫類別[value_compare](../standard-library/value-compare-class.md)的儲存雜湊*特性*物件，排序它所控制的序列。 藉由呼叫成員函式 [key_comp](#key_comp)，即可存取這個預存物件。 這類函式物件的行為必須與類別 [hash_compare](../standard-library/hash-compare-class.md)<索引鍵的物件相同，較不 \<Key>>。 尤其是針對*key*類型的所有值索引*鍵*，呼叫 `Traits` ( `Key` ) 會產生類型值的分佈 `size_t` 。

通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 f (x y) 是具有兩個引數物件 `x` 和以及傳回 `y` 值或的函式 **`true`** 物件 **`false`** 。 如果二元述詞為非自反、非對稱且可轉移的，而且如果等價是可轉移的，其中兩個物件 x 和 y 在 f(x, y) 和 f(y, x) 為 false 時定義為相等，則施加於 hash_map 的順序是嚴格弱式順序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。

受控制序列中實際的項目順序取決於雜湊函式、排序函式以及儲存於此容器物件中雜湊資料表目前的大小。 您無法判斷目前雜湊資料表的大小，因此一般而言，無法預測受控制序列中項目的順序。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。

hash_map 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#insert) 和 [hash_map](#hash_map) 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的一組需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通迭代器 `[First, Last)` 範圍。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[hash_map](#hash_map)|建構一個空的 `hash_map`，或是其他 `hash_map` 的全部或部分複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|類型，表示 `allocator` 物件的 `hash_map` 類別。|
|[const_iterator](#const_iterator)|一種類型，提供可讀取中專案的雙向反覆運算器 **`const`** `hash_map` 。|
|[const_pointer](#const_pointer)|一種類型，提供 **`const`** 中的元素指標 `hash_map` 。|
|[const_reference](#const_reference)|一種類型，提供 **`const`** 儲存在中的元素參考，以 `hash_map` 供讀取和執行 **`const`** 作業。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可讀取中任何元素的雙向反覆運算器 **`const`** `hash_map` 。|
|[difference_type](#difference_type)|帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中 `hash_map` 的項目數。|
|[迭 代](#iterator)|類型，其提供可讀取或修改 `hash_map` 中任何項目的雙向迭代器。|
|[key_compare](#key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `hash_map` 中的相對順序。|
|[key_type](#key_type)|類型，描述構成 `hash_map` 每個項目的排序鍵物件。|
|[mapped_type](#mapped_type)|類型，表示儲存在 `hash_map` 中的資料類型。|
|[指標](#pointer)|類型，其提供 `hash_map` 中項目的指標。|
|[reference](#reference)|類型，提供儲存在 `hash_map` 中之項目的參考。|
|[reverse_iterator](#reverse_iterator)|類型，提供可以讀取或修改反轉 `hash_map` 中之項目的雙向迭代器。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `hash_map` 中的項目數。|
|[value_type](#value_type)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `hash_map` 中的相對順序。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[at](#at)|在 `hash_map` 尋找具有指定索引鍵值的項目。|
|[開始](#begin)|傳回迭代器，為 `hash_map` 中的第一個項目定址。|
|[cbegin](#cbegin)|傳回常數迭代器，為 `hash_map` 中的第一個項目定址。|
|[cend](#cend)|傳回常數迭代器，為 `hash_map` 中最後一個項目的下一個位置定址。|
|[清楚](#clear)|清除 `hash_map` 的所有項目。|
|[計數](#count)|傳回 `hash_map` 中索引鍵符合參數指定之索引鍵的項目數目。|
|[crbegin](#crbegin)|傳回常數迭代器，為反轉 `hash_map` 中的第一個項目定址。|
|[crend](#crend)|傳回常數迭代器，為反轉 `hash_map` 中最後一個項目的下一個位置定址。|
|[emplace](#emplace)|將就地建構的項目插入 `hash_map` 中。|
|[emplace_hint](#emplace_hint)|將就地建構的項目 (含位置提示) 插入 `hash_map` 中。|
|[empty](#empty)|測試 `hash_map` 是否為空白。|
|[結束](#end)|傳回迭代器，為 `hash_map` 中最後一個項目的下一個位置定址。|
|[equal_range](#equal_range)|傳回一組迭代器，分別指向 `hash_map` 中索引鍵大於特定索引鍵的第一個項目，以及指向 `hash_map` 中索引鍵等於或大於該索引鍵的第一個項目。|
|[erase](#erase)|從指定位置移除在 `hash_map` 中的項目或某個範圍的項目。|
|[find](#find)|傳回迭代器，為 `hash_map` 中索引鍵等於指定索引鍵項目位置定址。|
|[get_allocator](#get_allocator)|傳回用來建構 `allocator` 的 `hash_map` 物件複本。|
|[insert](#insert)|將項目或項目範圍插入至 `hash_map`。|
|[key_comp](#key_comp)|傳回迭代器，指向 `hash_map` 中索引鍵值等於或大於特定索引鍵值的第一個項目。|
|[lower_bound](#lower_bound)|傳回迭代器，指向 `hash_map` 中索引鍵值等於或大於特定索引鍵值的第一個項目。|
|[max_size](#max_size)|傳回 `hash_map` 的最大長度。|
|[rbegin](#rbegin)|傳回迭代器，為反轉 `hash_map` 中的第一個項目定址。|
|[rend](#rend)|傳回迭代器，為反轉 `hash_map` 中最後一個項目的下一個位置定址。|
|[size](#size)|傳回 `hash_map` 中項目的數目。|
|[交換](#swap)|交換兩個 `hash_map` 的項目。|
|[upper_bound](#upper_bound)|傳回迭代器，其會指向 `hash_map` 中索引鍵值大於特定索引鍵值的第一個項目。|
|[value_comp](#value_comp)|擷取 `hash_map` 中用於排序項目值之比較物件的複本。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[operator&#91;&#93;](#op_at)|將具有特定索引鍵值的項目插入 `hash_map` 中。|
|[hash_map::operator=](#op_eq)|用另一個 `hash_map` 的複本取代 `hash_map` 的項目。|

## <a name="requirements"></a>規格需求

**標頭：**\<hash_map>

**命名空間：** stdext

## <a name="hash_mapallocator_type"></a><a name="allocator_type"></a> hash_map：： allocator_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，代表 hash_map 物件的配置器類別。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>範例

如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="hash_mapat"></a><a name="at"></a> hash_map：： at

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

在 hash_map 中尋找具有指定索引鍵值的項目。

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
所要尋找之元素的索引鍵值。

### <a name="return-value"></a>傳回值

所找到項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，函式就會擲回 [out_of_range 類別](../standard-library/out-of-range-class.md)的物件。

### <a name="example"></a>範例

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="hash_mapbegin"></a><a name="begin"></a> hash_map：： begin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回定址 hash_map 中第一個元素的迭代器。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 hash_map 中的第一個元素，或空 hash_map 後面的位置。

### <a name="example"></a>範例

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_mapcbegin"></a><a name="cbegin"></a> hash_map：： cbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回常數迭代器，定址對象是 hash_map 中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

常數雙向迭代器，定址對象是 [hash_map](../standard-library/hash-map-class.md) 中的第一個元素，或空 `hash_map` 後面的位置。

### <a name="example"></a>範例

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="hash_mapcend"></a><a name="cend"></a> hash_map：： cend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回常數迭代器，定址對象是 hash_map 中最後一個元素後面的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

常數雙向迭代器，定址對象是 [hash_map](../standard-library/hash-map-class.md) 中最後一個元素後面的位置。 如果 `hash_map` 是空的，則 `hash_map::cend == hash_map::begin`。

### <a name="remarks"></a>備註

`cend` 是用來測試迭代器是否已到達其 `hash_map` 的結尾。

`cend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="hash_mapclear"></a><a name="clear"></a> hash_map：： clear

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

清除 hash_map 的所有項目。

```cpp
void clear();
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範 hash_map:clear 成員函式的用法。

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="hash_mapconst_iterator"></a><a name="const_iterator"></a> hash_map：： const_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供可讀取 hash_map 中元素的雙向反覆運算器 **`const`** 。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

`const_iterator`由 hash_map 所定義的會指向屬於[value_type](#value_type)之物件的專案， `pair< const Key, Type >` 其第一個成員是專案的索引鍵，而第二個成員是元素所持有的對應基準。

若要對 `const_iterator` `cIter` 指向 hash_map 中某個元素的取值，請使用 `->` 運算子。

若要存取元素的索引鍵值，請使用 `cIter->first` 相當於的 `(*cIter).first` 。 若要存取專案的對應基準值，請使用 `cIter->second` 相當於的 `(*cIter).second` 。

### <a name="example"></a>範例

如需使用 `const_iterator` 的範例，請參閱 [begin](#begin) 的範例。

## <a name="hash_mapconst_pointer"></a><a name="const_pointer"></a> hash_map：： const_pointer

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供 **`const`** hash_map 中的元素指標。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 hash_map 物件中的元素。

## <a name="hash_mapconst_reference"></a><a name="const_reference"></a> hash_map：： const_reference

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供 **`const`** 儲存在 hash_map 中的元素參考，以讀取和執行 **`const`** 作業。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="hash_mapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_map：： const_reverse_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供可讀取 hash_map 中任何元素的雙向反覆運算器 **`const`** 。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 hash_map。

`const_reverse_iterator`由 hash_map 所定義的會指向屬於[value_type](#value_type)之物件的專案， `pair` \< **const Key, Type**> 其第一個成員是專案的索引鍵，而第二個成員是元素所持有的對應基準。

若要對指向 hash_map 中某個元素的 `const_reverse_iterator` `crIter` 進行取值，請使用 **->** 運算子。

若要存取該元素的索引鍵值，請使用 `crIter` -> **first**，這等同於 (\* `crIter`) **.first**。 若要存取該元素的已對應資料值，請使用 `crIter` -> **second**，這等同於 (\* `crIter`). **first**。

### <a name="example"></a>範例

如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#rend) 的範例。

## <a name="hash_mapcount"></a><a name="count"></a> hash_map：： count

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回 hash_map 中索引鍵符合參數指定之索引鍵的元素數目。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要從 hash_map 中比對之元素的索引鍵值。

### <a name="return-value"></a>傳回值

如果 hash_map 包含排序索引鍵符合參數索引鍵的元素則為 1；如果 hash_map 不含具有相符索引鍵的元素則為 0。

### <a name="remarks"></a>備註

成員函式會傳回下列範圍中的元素數目 *x*

\[ lower_bound (*金鑰*) ，upper_bound (*金鑰*) ) 

這在 hash_map (這是唯一的關聯容器) 的案例中是 0 或 1。

### <a name="example"></a>範例

下列範例示範如何使用 hash_map::count 成員函式。

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_mapcrbegin"></a><a name="crbegin"></a> hash_map：： crbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回常數迭代器，定址對象是反轉 hash_map 中的第一個元素。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [hash_map](../standard-library/hash-map-class.md) 中的第一個元素，或未反轉 `hash_map` 中的最後一個元素。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 hash_map 搭配使用，就如同 [begin](#begin) 是與 `hash_map` 搭配使用一樣。

有 `crbegin` 的傳回值時，無法修改 `hash_map` 物件。

`crbegin` 可用來向後逐一查看 `hash_map`。

### <a name="example"></a>範例

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapcrend"></a><a name="crend"></a> hash_map：： crend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回常數迭代器，定址對象是反轉 hash_map 中最後一個元素後面的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [hash_map](../standard-library/hash-map-class.md) 中最後一個元素後面的位置 (未反轉 `hash_map` 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 `hash_map` 搭配使用，就如同 [hash_map::end](#end) 是與 `hash_map` 搭配使用一樣。

有 `crend` 的傳回值時，無法修改 `hash_map` 物件。

`crend` 可以用來測試反轉迭代器是否已到達其 `hash_map` 的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapdifference_type"></a><a name="difference_type"></a> hash_map：:d ifference_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 hash_map 的元素數目。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>範例

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="hash_mapemplace"></a><a name="emplace"></a> hash_map：： emplace

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

將就地建構的元素插入到 hash_map 中。

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
用來移動建構要插入到 [hash_map](../standard-library/hash-map-class.md) 中之元素的值，除非 `hash_map` 已經包含該元素 (或更廣泛地說，即索引鍵以同等方式排序的元素)。

### <a name="return-value"></a>傳回值

`emplace` 成員函式會傳回一個配對，如果已進行插入，此配對的 bool 元件就會傳回 true，如果 `hash_map` 已經包含元素，其中該元素的索引鍵具有對等的排序值，且其 iterator 元件傳回新元素的插入位址或元素已在的位址，則會傳回 false。

若要存取此成員函式所傳回之配對 `pr` 的 iterator 元件，請使用 `pr.first`，若要取其值，請使用 `*(pr.first)`。 若要存取 **`bool`** 此成員函式所傳回之配對的元件 `pr` ，請使用 `pr.second` ，並使用來取值 `*(pr.second)` 。

### <a name="remarks"></a>備註

元素的 [hash_map::value_type](#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

### <a name="example"></a>範例

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_mapemplace_hint"></a><a name="emplace_hint"></a> hash_map：： emplace_hint

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

將就地建構的元素 (含位置提示) 插入到 hash_map 中。

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
用來移動建構要插入到 [hash_map](../standard-library/hash-map-class.md) 中之元素的值，除非 `hash_map` 已經包含該元素 (或更廣泛地說，即索引鍵以同等方式排序的元素)。

*_Where*\
一個有關要從哪裡開始搜尋正確插入點的提示。

### <a name="return-value"></a>傳回值

[hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) 成員函式會傳回迭代器，此迭代器指向新元素在 `hash_map` 中的插入位置，或具有對等排序之現有元素的所在位置。

### <a name="remarks"></a>備註

元素的 [hash_map::value_type](#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

如果插入點緊接著 *_Where*，則會在分攤的常數時間（而不是對數時間）進行插入。

### <a name="example"></a>範例

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_mapempty"></a><a name="empty"></a> hash_map：： empty

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

測試 hash_map 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 hash_map 空白，則為， **`false`** 如果 hash_map 不是空的。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="hash_mapend"></a><a name="end"></a> hash_map：： end

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，定址對象是 hash_map 中最後一個元素後面的位置。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 hash_map 中最後一個元素後面的位置。 如果 hash_map 是空的，則 hash_map::end == hash_map::begin。

### <a name="remarks"></a>備註

`end` 用來測試反覆運算器是否已到達其 hash_map 的結尾。

`end` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="hash_mapequal_range"></a><a name="equal_range"></a> hash_map：： equal_range

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回一組迭代器，分別指向 hash_map 中索引鍵大於指定索引鍵的第一個元素，以及指向 hash_map 中索引鍵等於或大於該索引鍵的第一個元素。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 hash_map 中元素的排序鍵比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

一組迭代器，其中第一個是索引鍵的 [lower_bound](#lower_bound)，第二個是索引鍵的 [upper_bound](#upper_bound)。

若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **首先** ，若要對下限反覆運算器進行取值，請使用 \* ( `pr` 。 **第一個**) 。 若要存取成員函式所傳回之配對 `pr` 的第二個迭代器，請使用 `pr`. **其次** ，若要取值上限反覆運算器，請使用 \* ( `pr` 。 **第二**) 。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="hash_maperase"></a><a name="erase"></a> hash_map：： erase

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

在 hash_map 中從指定位置移除一個項目或一連串項目，或移除符合指定之索引鍵的項目。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>參數

*_Where*\
要從 hash_map 中移除之項目的位置。

*第一*\
從 hash_map 中移除之第一個項目的位置。

*最後*\
從 hash_map 中移除的最後一個項目之後的位置。

*關鍵*\
要從 hash_map 中移除之項目的索引鍵值。

### <a name="return-value"></a>傳回值

在前兩個成員函式中，傳回雙向迭代器，其中指定任何移除的項目之外剩餘的第一個項目，或如果此項目不存在，則傳回 hash_map 結尾的指標。

在第三個成員函式中，傳回已從 hash_map 移除的項目數。

### <a name="remarks"></a>備註

成員函式永遠不會擲回例外狀況。

### <a name="example"></a>範例

下列範例示範 hash_map::erase 成員函式的用法。

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="hash_mapfind"></a><a name="find"></a> hash_map：： find

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，定址對象是 hash_map 中索引鍵等於指定索引鍵的元素位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要以所搜尋之 hash_map 中元素的排序鍵比對的索引鍵值。

### <a name="return-value"></a>傳回值

迭代器，定址對象是具有指定索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，則是 hash_map 中最後一個元素後面的位置。

### <a name="remarks"></a>備註

`find` 傳回反覆運算器，此反覆運算器會定址 hash_map 中的專案，其排序關鍵字相當於二元述詞下的引數索引鍵，該二元述詞會根據小於可比較性的關聯引發排序。

如果的傳回值 `find` 已指派給 [const_iterator](#const_iterator)，則無法修改 hash_map 物件。 如果的傳回值 `find` 已指派給 [iterator](#iterator)，則可以修改 hash_map 物件

### <a name="example"></a>範例

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapget_allocator"></a><a name="get_allocator"></a> hash_map：： get_allocator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回一份用來建構 hash_map 的配置器物件複本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>傳回值

hash_map 所使用的配置器。

### <a name="remarks"></a>備註

hash_map 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_maphash_map"></a><a name="hash_map"></a> hash_map：： hash_map

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

建構一個空的 hash_map，或是某個其他 hash_map 之全部或部分複本的 hash_map。

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>參數

*鋁*\
要用於此 hash_map 物件的儲存體配置器類別，預設為 `Allocator` 。

*壓縮*\
類型為 const `Traits` 並用來排序 hash_map 中元素的比較函式，預設為 `hash_compare`。

*對*\
要從中複製所建構之對應的 hash_map。

*第一*\
要複製的元素範圍中第一個元素的位置。

*最後*\
超出要複製之元素範圍的第一個元素的位置。

*IList*\
initializer_list

### <a name="remarks"></a>備註

所有建構函式都會儲存一種配置器物件，此物件可管理 hash_map 的記憶體儲存，且之後藉由呼叫 [get_allocator](#get_allocator) 即可傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。

所有建構函式都會將其 hash_map 初始化。

所有建構函式都會儲存一個 `Traits` 類型的函式物件，此物件可用來在 hash_map 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#key_comp) 即可傳回此物件。

前三個函式會指定空的初始 hash_map，此外，第二個會指定比較函式的類型 (要用來建立元素順序的 *複合*) ，而第三個則明確地指定要使用的配置器類型 (*Al*) 。 關鍵字會 **`explicit`** 隱藏某些類型的自動類型轉換。

第四個函式會指定 hash_map *右邊*的複本。

接下來的三個建構函式會複製 hash_map 的範圍 `[First, Last)`，其中會以越來越明確的方式指定類別 `Traits` 的比較函式及配置器的類型。

最後一個函式會將 hash_map *右移*。

## <a name="hash_mapinsert"></a><a name="insert"></a> hash_map：： insert

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

將某個元素或某個範圍的元素插入到 hash_map。

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
要插入到 hash_map 中之元素的值，除非 hash_map 已經包含該元素 (或更廣泛地說，即索引鍵以同等方式排序的元素)。

*_Where*\
一個有關要從哪裡開始搜尋正確插入點的提示。

*第一*\
要從 hash_map 複製之第一個元素的位置。

*最後*\
緊接在要從 hash_map 複製之最後一個元素後面的位置。

### <a name="return-value"></a>傳回值

第一個 `insert` 成員函式會傳回一個配對，如果已進行插入，則 bool 元件會傳回 true，而如果 hash_map 已經包含一個專案，而該專案的索引鍵具有對等的排序值，且其 iterator 元件傳回插入新元素的位址或專案已經存在的位置，則會傳回 false。

若要存取此成員函式所傳回之配對 `pr` 的 iterator 元件，請使用 `pr`. **首先**，若要對其進行取值，請使用 \* ( `pr` 。 **第一個**) 。 若要存取 **`bool`** 此成員函式所傳回之配對的元件 `pr` ，請使用 `pr` 。 **其次**，若要進行取值，請使用 \* ( `pr` 。 **第二**) 。

第二個 `insert` 成員函式（提示版本）會傳回反覆運算器，指向新元素插入 hash_map 的位置。

最後兩個 `insert` 成員函式的行為與前兩個成員函式的行為相同，不同之處在于它們會將插入的值加以建立。

### <a name="remarks"></a>備註

元素的 [value_type](../standard-library/map-class.md#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

如果插入點緊接在 *_Where*的位置，則插入可能會針對插入的提示版本（而不是對數時間）進行分攤的常數時間。

第三個成員函式會將元素值的序列插入到與每個元素對應的 hash_map 中，而這些元素是由指定集合之範圍 *[First, Last)* 中的迭代器所定址。

### <a name="example"></a>範例

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
The element 10 already exists in hm1
with a key value of ((pr.first) -> first) = 1.
After the insertions, the elements of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
5 => 50
After the insertions, the elements of hm2 are:
2 => 20
10 => 100
3 => 30
4 => 40
After the move insertion, hm3 contains:
1 => a
After the move insertion, hm4 contains:
2 => b
```

## <a name="hash_mapiterator"></a><a name="iterator"></a> hash_map：： iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供可讀取或修改 hash_map 中任何元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>備註

`iterator`由 hash_map 所定義的會指向屬於[value_type](#value_type)之物件的專案， `pair<const Key, Type>` 其第一個成員是專案的索引鍵，而第二個成員是元素所持有的對應基準。

若要取值為 `Iter` 指向 multimap 中某個元素的反覆運算器，請使用 `->` 運算子。

若要存取元素的索引鍵值，請使用 `Iter->first` 相當於的 `(*Iter).first` 。 若要存取專案的對應基準值，請使用 `Iter->second` 相當於的 `(*Iter).second` 。

類型 `iterator` 可以用來修改元素的值。

### <a name="example"></a>範例

如需如何宣告和使用的範例，請參閱 [開頭](#begin) 的範例 `iterator` 。

## <a name="hash_mapkey_comp"></a><a name="key_comp"></a> hash_map：： key_comp

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

擷取一份用來排序 hash_map 中索引鍵的比較物件複本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 hash_map 用來排序其元素的函式物件。

### <a name="remarks"></a>備註

預存物件會定義成員函式

`bool operator( const Key& left, const Key&right );`

**`true`** 如果 `left` `right` 在排序次序中，則會傳回，而且不等於。

### <a name="example"></a>範例

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="hash_mapkey_compare"></a><a name="key_compare"></a> hash_map：： key_compare

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷對應中兩個元素的相對順序。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>備註

`key_compare` 與樣板參數 `Traits` 同義。

如需有關 `Traits` 的詳細資訊，請參閱 [hash_map 類別](../standard-library/hash-map-class.md)主題。

### <a name="example"></a>範例

如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#key_comp) 的範例。

## <a name="hash_mapkey_type"></a><a name="key_type"></a> hash_map：： key_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，描述構成 hash_map 每個元素的排序鍵物件。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

`key_type` 與樣板參數 `Key` 同義。

如需有關 `Key` 的詳細資訊，請參閱 [hash_map 類別](../standard-library/hash-map-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="hash_maplower_bound"></a><a name="lower_bound"></a> hash_map：： lower_bound

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，指向 hash_map 中索引鍵值等於或大於指定索引鍵值的第一個元素。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 hash_map 中元素的排序鍵比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

[iterator](#iterator) 或 [const_iterator](#const_iterator)，定址對象是 hash_map 中索引鍵等於或大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_map 中最後一個元素後面的位置。

如果將 `lower_bound` 的傳回值指派給 `const_iterator`，便無法修改 hash_map 物件。 如果的傳回值 `lower_bound` 已指派給 `iterator` ，則可以修改 hash_map 物件。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapmapped_type"></a><a name="mapped_type"></a> hash_map：： mapped_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，代表儲存在 hash_map 中的資料類型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>備註

類型 `mapped_type` 與範本參數 `Type` 同義。

如需有關 `Type` 的詳細資訊，請參閱 [hash_map 類別](../standard-library/hash-map-class.md)主題。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="hash_mapmax_size"></a><a name="max_size"></a> hash_map：： max_size

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回 hash_map 的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

hash_map 的最大可能長度。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="hash_mapoperator"></a><a name="op_at"></a> hash_map：： operator []

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

將具有特定索引鍵值的項目插入 `hash_map` 中。

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>參數

*關鍵*\
所要插入之元素的索引鍵值。

### <a name="return-value"></a>傳回值

所插入項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，則將它與資料類型的預設值一起插入。

`operator[]` 可用來將元素插入到 `hash_map m`，方法是使用

`m[ key] = DataValue`;

其中 DataValue 是索引鍵值 `mapped_type` 為 *key*之元素的值。

使用 `operator[]` 來插入元素時，傳回的參考不會指出插入是變更預先存在的元素，還是建立新的元素。 成員函式 [find](../standard-library/map-class.md#find) 和 [insert](../standard-library/map-class.md#insert) 可用來判斷具有指定索引鍵的元素在插入之前是否已經存在。

### <a name="example"></a>範例

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="hash_mapoperator"></a><a name="op_eq"></a> hash_map：： operator =

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

將 hash_map 的元素以另一個 hash_map 的複本取代。

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>參數

*對*\
要複製到 `hash_map` 中的 [hash_map 類別](../standard-library/hash-map-class.md)。

### <a name="remarks"></a>備註

清除中的任何現有元素之後 `hash_map` ，會 `operator=` 將 *右邊* 的內容複寫或移動到 `hash_map` 。

### <a name="example"></a>範例

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

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

## <a name="hash_mappointer"></a><a name="pointer"></a> hash_map：:p ointer

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供 hash_map 中元素的指標。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>備註

類型 `pointer` 可以用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 hash_map 物件中的元素。

## <a name="hash_maprbegin"></a><a name="rbegin"></a> hash_map：： rbegin

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，定址對象是反轉 hash_map 中的第一個元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 hash_map 中的第一個元素，或未反轉 hash_map 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 hash_map 搭配使用，就如同 [begin](#begin) 是與 hash_map 搭配使用一樣。

如果將 `rbegin` 的傳回值指派給 [const_reverse_iterator](#const_reverse_iterator)，便無法修改 hash_map 物件。 如果將 `rbegin` 的傳回值指派給 [reverse_iterator](#reverse_iterator)，則可以修改 hash_map 物件。

`rbegin` 可用來向後逐一查看 hash_map。

### <a name="example"></a>範例

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="hash_mapreference"></a><a name="reference"></a> hash_map：： reference

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供對儲存在 hash_map 中元素的參考。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="hash_maprend"></a><a name="rend"></a> hash_map：： rend

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，定址對象是反轉 hash_map 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 hash_map 中最後一個元素後面的位置 (未反轉 hash_map 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 hash_map 搭配使用，就如同 [end](#end) 是與 hash_map 搭配使用一樣。

如果將 `rend` 的傳回值指派給 [const_reverse_iterator](#const_reverse_iterator)，便無法修改 hash_map 物件。 如果將 `rend` 的傳回值指派給 [reverse_iterator](#reverse_iterator)，則可以修改 hash_map 物件。

`rend` 可以用來測試反轉迭代器是否已到達其 hash_map 的結尾。

`rend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="hash_mapreverse_iterator"></a><a name="reverse_iterator"></a> hash_map：： reverse_iterator

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，提供可讀取或修改反轉 hash_map 中元素的雙向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 hash_map。

`reverse_iterator`由 hash_map 所定義的會指向屬於** \<const Key, Type> **類型[value_type](#value_type)之物件的專案，其第一個成員是專案的索引鍵，而第二個成員是元素所持有的對應基準。

若要對指向 hash_map 中某個元素的 `reverse_iterator` `rIter` 進行取值，請使用 -> 運算子。

若要存取該元素的索引鍵值，請使用 `rIter` -> **first**，這等同於 (\* `rIter`). **first**。 若要存取該元素的已對應資料值，請使用 `rIter` -> **second**，這等同於 (\* `rIter`). **first**。

### <a name="example"></a>範例

如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#rbegin) 的範例。

## <a name="hash_mapsize"></a><a name="size"></a> hash_map：： size

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回 hash_map 中的元素數。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

hash_map 的目前長度。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範 hash_map::size 成員函式的用法。

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="hash_mapsize_type"></a><a name="size_type"></a> hash_map：： size_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種不帶正負號的整數類型，可代表 hash_map 中的元素數目。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>備註

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例。

## <a name="hash_mapswap"></a><a name="swap"></a> hash_map：： swap

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

交換兩個 hash_map 的元素。

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>參數

*對*\
提供要與目標 hash_map 交換之元素的引數 hash_map。

### <a name="remarks"></a>備註

任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 hash_map 中，成員函式就不會使其失效。

### <a name="example"></a>範例

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="hash_mapupper_bound"></a><a name="upper_bound"></a> hash_map：： upper_bound

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回迭代器，指向 hash_map 中索引鍵值大於指定索引鍵值的第一個元素。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*關鍵*\
要與所搜尋之 hash_map 中元素的排序鍵值比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

[iterator](#iterator) 或 [const_iterator](#const_iterator)，定址對象是 hash_map 中索引鍵大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_map 中最後一個元素後面的位置。

如果將傳回值指派給 `const_iterator`，便無法修改 hash_map 物件。 如果將傳回值指派給 `iterator` ，則可以修改 hash_map 物件。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="hash_mapvalue_comp"></a><a name="value_comp"></a> hash_map：： value_comp

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

傳回函式物件，此物件可藉由比較 hash_map 中元素的索引鍵值來判斷這些元素的順序。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 hash_map 用來排序其元素的比較函式物件。

### <a name="remarks"></a>備註

針對 hash_map *m*，如果有兩個元素*e1* (*版 k1*、 *d1*) 和*e2* (*k2*，則*d2*) 是類型[value_type 的物件，其中](#value_type)*版 k1*和*k2*是其類型的索引鍵[，而](#key_type) *d1*和*d2*是其[類型的資料 key_type，則](#mapped_type) `m.value_comp()(e1, e2)` 相當於 `m.key_comp()(k1, k2)` 。 預存物件會定義成員函式

`bool operator(value_type& left, value_type& right);`

如果的索引鍵值 **`true`** `left` 早于，且 `right` 在排序次序中不等於的索引鍵值，則會傳回此值。

### <a name="example"></a>範例

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_mapvalue_type"></a><a name="value_type"></a> hash_map：： value_type

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

一種類型，代表儲存在 hash_map 中的物件類型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>備註

`value_type` 宣告為 `pair<const key_type, mapped_type>` ，而不是 `pair<key_type, mapped_type>` 因為關聯容器的索引鍵可能不會使用非常數反覆運算器或參考來變更。

### <a name="example"></a>範例

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
