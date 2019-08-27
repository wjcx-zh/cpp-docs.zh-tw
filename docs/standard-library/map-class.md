---
title: map 類別
ms.date: 10/18/2018
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
ms.openlocfilehash: 22bb9d94b4c420419941a5bb7af24009b91f0a54
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456312"
---
# <a name="map-class"></a>map 類別

從每個項目都是資料值與排序鍵組的集合，用於資料儲存和擷取。 索引鍵的值是唯一的，用於自動排序資料。

對應中的項目值可以直接變更。 索引鍵值是常數，無法變更。 相反地，與舊項目相關聯的索引鍵值必須刪除，並插入新項目的新索引鍵值。

## <a name="syntax"></a>語法

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>參數

*擊鍵*\
要存放在對應中的索引鍵資料類型。

*型*\
要存放在對應中的項目資料類型。

*共同*\
類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在對應中的相對順序。 這個引數是選用引數，且預設值是二元述詞 `less<Key>`。

在 C++14 中，指定沒有型別參數的 std::less<> 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)。

*配置器*\
代表預存配置器物件的類型，封裝有關對應之記憶體配置和解除配置的詳細資訊。 這個引數是選擇性的，而且預設值是 `allocator<pair<const Key, Type> >`。

## <a name="remarks"></a>備註

「C++ 標準程式庫」map 類別是：

- 可變大小的容器，根據關聯的索引鍵值，有效率地擷取項目值。

- 可逆轉的，因為它提供雙向的迭代器以存取其項目。

- 已排序，因為其項目是依據指定的比較函式，由索引鍵值排序。

- 唯一。 因為其項目都必須具有唯一索引鍵。

- 一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。

- 樣板類別，因為它提供的功能是泛型，且與項目或索引鍵類型無關。 用於項目和索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。

map 類別提供的迭代器是雙向迭代器，但 [insert](#insert) 和 [map](#map) 類別成員函式擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而有關聯性。 每個迭代器概念有自己的一組需求，因此搭配使用的演算法受那些需求所限制。 輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。

建議您根據應用程式所需的搜尋和插入種類，來選擇容器類型。 關聯的容器已針對查閱、插入和移除作業最佳化。 明確支援這些作業的成員函式以最糟狀況時間執行它們 (此時間與容器中的項目數目之對數成正比)。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。

當關聯值與索引鍵的條件由應用程式滿足時，我們建議您選擇使用對應做為關聯容器。 這種結構的模型是已排序的唯一關鍵字清單，其中關聯的字串值提供定義。 如果文字具有一個以上的正確定義，並且索引鍵不是唯一的，則多重對應是首選容器。 如果正是要儲存文字清單，則集合將是適當的容器。 如果允許文字的多個項目，則多重集較為適當。

map 會藉由呼叫 [key_compare](#key_compare) 類型的預存函式物件，排序它所控制的元素。 這個預存物件是可藉由呼叫 [key_comp](#key_comp) 方法來存取的比較函式。 一般而言，任何兩個特定項目會進行比較，判斷一個是否小於另一個或兩者是否相等。 當比較所有項目，會建立已排序的非對等項目序列。

> [!NOTE]
> 比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 f (x, y) 是有兩個引數物件 x 和 y 以及傳回值**true**或**false**的函式物件。 如果二元述詞是非反、對稱性和可轉移的, 則強加于集合的順序就是嚴格弱式排序, 而且如果等價是可轉移的, 當 f (x, y) 和 f (y, x) 都是**false**時, 會將兩個 x 和 y 的物件定義為相等。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。
>
> 在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[map](#map)|建構特定大小的清單，或具有特定值之項目的清單，或具有特定 `allocator` 的清單，或是做為其他對應的複本。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|對應物件之 `allocator` 類別的 typedef。|
|[const_iterator](#const_iterator)|雙向反覆運算器的 typedef, 可以讀取對應中的**const**元素。|
|[const_pointer](#const_pointer)|對應中**const**元素指標的 typedef。|
|[const_reference](#const_reference)|對應中儲存之**const**元素的參考的 typedef, 用於讀取和執行**const**運算。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可讀取 map 中任何 **const** 元素的雙向迭代器。|
|[difference_type](#difference_type)|範圍 (介於迭代器所指的項目) 中對應的項目數量的帶正負號整數 typedef。|
|[iterator](#iterator)|雙向迭代器的 typedef，可以讀取或修改對應中的任何項目。|
|[key_compare](#key_compare)|函式物件之 typedef，可比較兩個排序鍵以判斷兩個項目在對應中的相對順序。|
|[key_type](#key_type)|對應中每個項目所儲存之排序鍵的 typedef。|
|[mapped_type](#mapped_type)|對應中每個項目所儲存之資料的 typedef。|
|[pointer](#pointer)|對應中**const**元素指標的 typedef。|
|[reference](#reference)|對應中預存項目的參考之 typedef。|
|[reverse_iterator](#reverse_iterator)|雙向迭代器的 typedef，可以讀取或修改反轉對應中的項目。|
|[size_type](#size_type)|不帶正負號的整數 typedef，表示對應中的項目數。|
|[value_type](#value_type)|typedef，表示對應中儲存為項目的物件類型。|

### <a name="member-functions"></a>成員函式

|成員函式|說明|
|-|-|
|[at](#at)|尋找具有指定之索引鍵值的項目。|
|[begin](#begin)|傳回指向對應中的第一個項目的迭代器。|
|[cbegin](#cbegin)|傳回指向對應中的第一個項目的常數迭代器。|
|[cend](#cend)|傳回常數超出結尾 (past-the-end) 迭代器。|
|[clear](#clear)|清除對應的所有項目。|
|[計數](#count)|傳回對應中索引鍵符合參數所指定之索引鍵的項目數目。|
|[crbegin](#crbegin)|傳回指向反轉對應中的第一個項目的常數迭代器。|
|[crend](#crend)|傳回反轉對應中，指向最後一個項目後面的位置之常數迭代器。|
|[emplace](#emplace)|將就地建構的項目插入對應中。|
|[emplace_hint](#emplace_hint)|將就地建構的項目 (含位置提示) 插入對應中。|
|[empty](#empty)|如果對應是空的, 則傳回**true** 。|
|[end](#end)|傳回超出結尾 (past-the-end) 迭代器。|
|[equal_range](#equal_range)|傳回一對迭代器。 配對中第一個迭代器指向 `map` 中索引鍵大於指定索引鍵的第一個項目。 配對中第二個迭代器指向 `map` 中索引鍵等於或大於指定索引鍵的第一個項目。|
|[erase](#erase)|從對應中的指定位置移除項目或某個項目範圍。|
|[find](#find)|傳回迭代器，指向對應中索引鍵等於指定索引鍵的第一個項目的位置。|
|[get_allocator](#get_allocator)|傳回用於建構對應的 `allocator` 物件複本。|
|[insert](#insert)|在對應中的指定位置插入項目或某個項目範圍。|
|[key_comp](#key_comp)|傳回對應中用來排序索引鍵的比較物件之複本。|
|[lower_bound](#lower_bound)|傳回迭代器，指向對應中索引鍵值等於或大於特定索引鍵值的第一個項目。|
|[max_size](#max_size)|傳回對應的最大長度。|
|[rbegin](#rbegin)|傳回指向反轉對應中的第一個項目的迭代器。|
|[rend](#rend)|傳回反轉對應中，指向最後一個項目後面的位置之迭代器。|
|[size](#size)|傳回對應中項目的數目。|
|[swap](#swap)|交換兩個對應的項目。|
|[upper_bound](#upper_bound)|傳回迭代器，指向對應中索引鍵值大於特定索引鍵值的第一個項目。|
|[value_comp](#value_comp)|擷取對應中用於排序項目值的比較物件之複本。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator&#91;&#93;](#op_at)|將具有特定索引鍵值的項目插入對應中。|
|[operator=](#op_eq)|用另一個對應複本取代對應的項目。|

## <a name="allocator_type"></a>allocator_type

一種類型，代表 map 物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>範例

如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="at"></a>在

尋找具有指定之索引鍵值的項目。

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>參數

金鑰 * \
要尋找的索引鍵值。

### <a name="return-value"></a>傳回值

所找到項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，函式就會擲回 [out_of_range 類別](../standard-library/out-of-range-class.md)的物件。

### <a name="example"></a>範例

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a>起點

傳回迭代器，定址對象是 map 中的第一個元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，定址對象是 map 中的第一個元素，或空 map 後面的位置。

### <a name="example"></a>範例

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a> cbegin

傳回**常數**反覆運算器, 定址範圍中最後一個元素之後的位置。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**常數**雙向反覆運算器, 定址範圍中的第一個元素, 或為空白範圍結尾 (空白範圍`cbegin() == cend()`) 之外的位置。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中, `Container`請將視為支援`begin()`和`cbegin()`的任何種類的可修改 (非**const**) 容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

傳回**常數**反覆運算器, 定址範圍中最後一個元素之後的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的**const**雙向存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中, `Container`請將視為支援`end()`和`cend()`的任何種類的可修改 (非**const**) 容器。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a>明確

清除對應的所有項目。

```cpp
void clear();
```

### <a name="example"></a>範例

下列範例示範 map:clear 成員函式的用法。

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>const_iterator

一種類型，提供可讀取 map 中 **const** 元素的雙向迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

map 所定義的 `const_iterator` 會指向作為 [value_type](#value_type) 之物件的元素，value_type 的類型為 `pair`\< **constKey**, **Type**>，其第一個成員是元素的索引鍵，而第二個成員是該元素所持有的已對應資料。

若要對`const_iterator`指向對應中某個元素的`cIter`進行取值, 請`->`使用運算子。

若要存取該元素的索引鍵值，請使用 `cIter` -> **first**，這等同於 (\* `cIter`). **first**。

若要存取該元素的已對應資料值，請使用 `cIter` -> **second**，這等同於 (\* `cIter`). **second**。

### <a name="example"></a>範例

如需使用 `const_iterator` 的範例，請參閱 [begin](#begin) 的範例。

## <a name="const_pointer"></a>const_pointer

一種類型，提供 map 中 **const** 元素的指標。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 map 物件中的元素。

## <a name="const_reference"></a>const_reference

一種類型，提供對儲存在 map 中以供讀取和執行 **const** 運算之 **const** 元素的參考。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>範例

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

一種類型，提供可讀取 map 中任何 **const** 元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 map。

由`const_reverse_iterator`對應定義的會指向專案, 這些專案是[value_type](#value_type)的物件 (其為`pair<const Key, Type>`類型), 其第一個成員是專案的索引鍵, 而第二個成員是元素所持有的對應基準。

若要對`const_reverse_iterator crIter`指向對應中某個元素的進行取值, 請`->`使用運算子。

若要存取元素的索引鍵值, 請使用`crIter` \*  ->  **first**, 這相當於 ( `crIter`)。**首先**。

若要存取專案的對應基準值, 請使用`crIter` \*  ->  **second**, 這相當於 ( `crIter`)。**首先**。

### <a name="example"></a>範例

如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#rend) 的範例。

## <a name="count"></a>計數

傳回對應中索引鍵符合參數指定之索引鍵的項目數。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要從對應中比對之項目的索引鍵值。

### <a name="return-value"></a>傳回值

如果對應包含排序索引鍵符合參數索引鍵的項目則為 1；如果對應不含具有相符索引鍵的項目則為 0。

### <a name="remarks"></a>備註

成員函式會傳回下列範圍中的元素數目 *x*

\[ lower_bound(*key*), upper_bound(*key*) )

，其為對應案例中的 0 或 1，且是唯一相關聯的容器。

### <a name="example"></a>範例

下列範例示範如何使用 map::count 成員函式。

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
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
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>crbegin

傳回常數迭代器，定址對象是反轉 map 中的第一個元素。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [map](../standard-library/map-class.md) 中的第一個元素，或未反轉 `map` 中的最後一個元素。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 `map` 搭配使用，就如同 [begin](#begin) 是與 `map` 搭配使用一樣。

有 `crbegin` 的傳回值時，無法修改 `map` 物件。

`crbegin` 可用來向後逐一查看 `map`。

### <a name="example"></a>範例

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>crend

傳回常數迭代器，定址對象是反轉 map 中最後一個元素後面的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [map](../standard-library/map-class.md) 中最後一個元素後面的位置 (未反轉 `map` 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 map 搭配使用，就如同 [end](#end) 是與 `map` 搭配使用一樣。

有 `crend` 的傳回值時，無法修改 `map` 物件。

`crend` 可以用來測試反轉迭代器是否已到達其 `map` 的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>difference_type

一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 map 的元素數目。

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 `first` 和 `last` 之間範圍 *[ first,  last)* 內的元素數目，包括 `first` 所指的元素以及上限到 `last` 所指元素 (但不包含此元素) 的元素範圍。

請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別，但只有隨機存取容器 (例如 vector) 所提供的隨機存取迭代器，才支援迭代器之間的減法。

### <a name="example"></a>範例

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>emplace

將就地建構 (未執行任何複製或移動作業) 的元素插入到 map 中。

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>參數

*引數*\
轉送以建構插入 unordered_map 之元素的引數，除非它已經包含一個值以同等方式排序的元素。

### <a name="return-value"></a>傳回值

如果已進行插入, 則為**bool**元件為 true 的[配對](../standard-library/pair-structure.md), 如果對應已包含排序中的對等值的元素, 則為 false。 如果**bool**元件為 true, 傳回值組的反覆運算器元件會指向新插入的元素; 如果**bool**元件為 false, 則會指向現有的元素。

若要存取的反覆運算器元件`pair` `pr`, 請`pr.first`使用; 若要對其`*pr.first`進行取值, 請使用。 若要存取**bool**元件, 請`pr.second`使用。 例如，請參閱本文中稍後的範例程式碼。

### <a name="remarks"></a>備註

此函式不會使任何迭代器或參考失效。

在定位期間，如果擲回例外狀況，就不會修改容器的狀態。

元素的 [value_type](#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

### <a name="example"></a>範例

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

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
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a>emplace_hint

將就地建構 (未執行任何複製或移動作業) 的項目連同位置提示一起插入。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>參數

*引數*\
所轉接以建構要插入到對應中之元素的引數，除非該對應中已經包含該元素，或更廣泛地說，即除非它已經包含索引鍵以同等方式排序的元素。

*希望*\
要開始搜尋正確的插入點的地方。 (如果該點緊接在*位置*之前, 則會在分攤常數時間中進行插入, 而不是對數時間)。

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

如果因為元素已經存在而插入失敗，便會傳回指向現有元素及其索引鍵的迭代器。

### <a name="remarks"></a>備註

此函式不會使任何迭代器或參考失效。

在定位期間，如果擲回例外狀況，就不會修改容器的狀態。

元素的 [value_type](#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

### <a name="example"></a>範例

```cpp
// map_emplace.cpp
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
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="empty"></a>空

測試 map 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果 map 是空的，即為 **true**；如果 map 不是空的，則為 **false**。

### <a name="example"></a>範例

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>成品

傳回超出結尾 (past-the-end) 迭代器。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

超出結尾迭代器。 如果 map 是空的，則 `map::end() == map::begin()`。

### <a name="remarks"></a>備註

`end`是用來測試反覆運算器是否已超過其對應的結尾。

`end` 所傳回的值不應該取值。

如需程式碼範例，請參閱 [map::find](#find)。

## <a name="equal_range"></a>equal_range

傳回一組迭代器，分別代表索引鍵的 [lower_bound](#lower_bound) 和索引鍵的 [upper_bound](#upper_bound)。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之對應中元素的排序鍵比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之 `pr` 配對的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。

### <a name="example"></a>範例

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>抹

從 map 中指定的位置移除某個元素或某個範圍的元素，或移除符合指定索引鍵的元素。

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

*希望*\
要移除之項目的位置。

*頭*\
要移除之第一個項目的位置。

*次*\
緊接在要移除之最後一個項目後面的位置。

*擊鍵*\
要移除之項目的索引鍵值。

### <a name="return-value"></a>傳回值

針對前兩個成員函式，會傳回雙向迭代器，其中指定任何移除之元素後剩餘的第一個元素，或如果沒有這類元素，則傳回 map 結尾的元素。

針對第三個成員函式，會傳回已從 map 移除的元素數目。

### <a name="example"></a>範例

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an initializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}
```

## <a name="find"></a>尋找

傳回迭代器，參考對象是 map 中索引鍵等於指定索引鍵的元素位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要以所搜尋之 map 中元素的排序鍵比對的索引鍵值。

### <a name="return-value"></a>傳回值

反覆運算器, 參考具有指定之索引鍵的元素位置, 或如果找不到索引鍵的相符專案, 則為`map::end()`map 中最後一個元素後面的位置 ()。

### <a name="remarks"></a>備註

成員函式會傳回迭代器，參考對象是 map 中，在根據小於可比較性關聯來引發排序的二元述詞下，其排序鍵等於引數索引鍵的元素。

如果將 `find` 的傳回值指派給 `const_iterator`，便無法修改 map 物件。 如果將的傳回值`find`指派`iterator`給, 則可以修改 map 物件。

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
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
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

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a> get_allocator

傳回一份用來建構 map 的配置器物件複本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

map 所使用的配置器。

### <a name="remarks"></a>備註

map 類別的配置器會指定此類別管理儲存體的方式。 「C++ 標準程式庫」容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>插入

將某個項目或項目範圍插入對應中。

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

*初始值*\
除非其中包含了索引鍵已經過對等地排序的項目，否則為要插入對應中的項目值。

*希望*\
要開始搜尋正確的插入點的地方。 (如果該點緊接在*位置*之前, 則會在分攤常數時間中進行插入, 而不是對數時間)。

*ValTy*\
範本參數, 指定對應可用來建立[value_type](#value_type)的元素的引數類型, 並將*Val*當做引數完美轉送。

*頭*\
要複製之第一個元素的位置。

*次*\
要複製之最一個元素後方的位置。

*InputIterator*\
符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](#value_type) 物件的類型。

*IList*\
要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。

### <a name="return-value"></a>傳回值

單一元素成員函式 (1) 和 (2) 會傳回一個[配對](../standard-library/pair-structure.md), 如果已進行插入, 則其**bool**元件為 true, 如果對應已包含索引鍵在順序中具有對等值的專案, 則為 false。 如果**bool**元件為 true, 傳回值組的反覆運算器元件會指向新插入的元素; 如果**bool**元件為 false, 則會指向現有的元素。

具有提示的單一項目成員函式 (3) 及 (4) 會傳回指向位置的迭代器，該位置是新項目插入對應中的位置，或者，若對等索引鍵已存在，則指向現有項目。

### <a name="remarks"></a>備註

此函式不會使任何迭代器、指標或參考無效。

在只插入一個元素的期間，若擲出例外狀況，則不會修改容器的狀態。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。

若要存取 `pair` `pr` 的迭代器元件 (由單一元素成員函式傳回)，請使用 `pr.first`；若要對傳回的 pair 中的迭代器取值，請使用 `*pr.first` (提供您元素)。 若要存取**bool**元件, 請`pr.second`使用。 例如，請參閱本文中稍後的範例程式碼。

容器的 [value_type](#value_type) 是屬於容器的 typedef，而就 map 而言，`map<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

範圍成員函式 (5) 會將項目值的序列插入對應至每個項目的對應，而這些項目是由範圍 `[First, Last)` 中的迭代器指定；因此不會插入 `Last`。 容器成員函式 `end()` 會參考容器中最後一個項目之後的位置。例如陳述式 `m.insert(v.begin(), v.end());` 嘗試將 `v` 的所有項目插入 `m`。 只會插入具有範圍中唯一值的元素；若重複則會忽略。 若要觀察哪些元素會遭到拒絕，請使用單一元素版本的 `insert`。

初始設定式清單成員函式 (6) 會使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 map。

針對插入就地建構 (也就是未執行任何複製或移動作業) 的元素，請參閱 [map::emplace](#emplace) 和 [map::emplace_hint](#emplace_hint)。

### <a name="example"></a>範例

```cpp
// map_insert.cpp
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
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
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
    map<int, string>  m3;
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

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a>定位

一種類型，提供可讀取或修改 map 中任何元素的雙向迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

對應所定義的反覆運算器會指向屬於[value_type](#value_type)物件的元素, 其類型`pair<const Key, Type>`為, 其第一個成員是專案的索引鍵, 而第二個成員是元素所持有的對應基準。

若要對指向對應中某個元素的反覆運算器*Iter*取值, 請`->`使用運算子。

若要存取元素的索引鍵值, 請使用`Iter->first`, 這相當於。 `(*Iter).first` 若要存取專案的對應基準值, 請使用`Iter->second`, 這相當於。 `(*Iter).second`

### <a name="example"></a>範例

如需如何[](#begin)宣告和使用`iterator`的範例, 請參閱 begin 的範例。

## <a name="key_comp"></a>key_comp

擷取一份用來排序 map 中索引鍵的比較物件複本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 map 用來排序其元素的函式物件。

### <a name="remarks"></a>備註

預存物件會定義成員函式

`bool operator(const Key& left, const Key& right);`

如果 `left` 在前面且在排序次序中不等於 `right`，此函式就會傳回 **true**。

### <a name="example"></a>範例

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
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

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
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

## <a name="key_compare"></a>key_compare

一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷對應中兩個元素的相對順序。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>備註

`key_compare`是範本參數*特性*的同義字。

如需有關*特性*的詳細資訊, 請參閱[map 類別](../standard-library/map-class.md)主題。

### <a name="example"></a>範例

如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#key_comp) 的範例。

## <a name="key_type"></a>key_type

一種類型，描述儲存在 map 每個元素中的排序鍵。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

`key_type`是範本參數索引*鍵*的同義字。

如需*金鑰*的詳細資訊, 請參閱[map 類別](../standard-library/map-class.md)主題的「備註」一節。

### <a name="example"></a>範例

如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="lower_bound"></a>lower_bound

傳回迭代器，指向 map 中索引鍵值等於或大於指定索引鍵值的第一個元素。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之對應中元素的排序鍵比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

`iterator` 或`const_iterator` , 定址對應中索引鍵等於或大於引數索引鍵的元素位置, 或者, 如果找不到與該索引鍵相符的專案, 則定址對應中最後一個元素後面的位置。

如果將 `lower_bound` 的傳回值指派給 `const_iterator`，便無法修改 map 物件。 如果將的傳回值`lower_bound`指派`iterator`給, 則可以修改 map 物件。

### <a name="example"></a>範例

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>地圖

建構一個空的 map，或是某個其他 map 之全部或部分複本的 map。

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>參數

*Al*\
要用於此 map 物件的儲存體配置器類別，預設為 `Allocator`。

*背光*\
類型為 `const Traits` 並用來排序 map 中元素的比較函式，預設為 `hash_compare`。

*再*\
要從中複製所建構之集合的對應。

*頭*\
要複製的元素範圍中第一個元素的位置。

*次*\
超出要複製之元素範圍的第一個元素的位置。

*IList*\
要從中複製元素的 initializer_list。

### <a name="remarks"></a>備註

所有建構函式都會儲存一種配置器物件，此物件可管理 map 的記憶體儲存，且之後藉由呼叫 [get_allocator](#get_allocator) 即可傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。

所有建構函式都會將其 map 初始化。

所有建構函式都會儲存一個 Traits 類型的函式物件，此物件可用來在 map 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#key_comp) 即可傳回此物件。

前三個函式會指定空的初始對應, 第二個是指定要用來建立元素順序的比較函數 (*Comp*) 類型, 而第三個是明確指定要使用的配置器類型 (*Al*)。 關鍵字**explicit**會隱藏某些類型的自動類型轉換。

第四個函式會指定地圖*右邊*的複本。

第五個函式會藉由*向右*移動來指定對應的複本。

第六、第七及第八個建構函式會使用 initializer_list 來從中複製成員。

接下來的三個建構函式會複製 map 的範圍 `[First, Last)`，其中會以越來越明確的方式指定類別 `Traits` 的比較函式及配置器的類型。

### <a name="example"></a>範例

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of greater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
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

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}
```

## <a name="mapped_type"></a>mapped_type

一種類型，代表儲存在 map 中的資料。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>備註

此類型`mapped_type`與類別的*類型*樣板參數同義。

如需*類型*的詳細資訊, 請參閱[map 類別](../standard-library/map-class.md)主題。

### <a name="example"></a>範例

如需如何宣告及使用 `mapped_type` 的範例，請參閱 [value_type](#value_type) 的範例。

## <a name="max_size"></a>max_size

傳回對應的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

map 的最大可能長度。

### <a name="example"></a>範例

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>operator []

將具有特定索引鍵值的項目插入對應中。

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>參數

*擊鍵*\
所要插入之元素的索引鍵值。

### <a name="return-value"></a>傳回值

所插入項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，則將它與資料類型的預設值一起插入。

`operator[]`可以用`m`來將專案插入對應`m[key] = DataValue;`中, 其中`DataValue`是具有索引鍵值的元素`mapped_type`之專案的值。

當使用 `operator[]` 插入項目時，傳回的參考不會指出插入是變更預先存在的項目，還是建立新的項目。 成員函式 [find](#find) 和 [insert](#insert) 可用來判斷具有指定索引鍵的元素在插入之前是否已經存在。

### <a name="example"></a>範例

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>operator =

用另一個對應複本取代對應的項目。

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>參數

*再*\
要複製到 `map` 中的 [map](../standard-library/map-class.md)。

### <a name="remarks"></a>備註

清除中的任何現有專案之後`map`, `operator=`會將*右邊*的內容複寫或移動到地圖中。

### <a name="example"></a>範例

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

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

## <a name="pointer"></a>滑鼠

一種類型，提供 map 中元素的指標。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>備註

類型`pointer`可用於修改元素的值。

在大多數情況下，應該使用 [iterator](#iterator) 來存取 map 物件中的元素。

## <a name="rbegin"></a>rbegin

傳回迭代器，定址對象是反轉 map 中的第一個元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 map 中的第一個元素，或未反轉 map 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 map 搭配使用，就如同 [begin](#begin) 是與 map 搭配使用一樣。

如果將 `rbegin` 的傳回值指派給 `const_reverse_iterator`，便無法修改 map 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改 map 物件。

`rbegin` 可用來向後逐一查看 map。

### <a name="example"></a>範例

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>證明

一種類型，提供對儲存在 map 中元素的參考。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>範例

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>rend

傳回迭代器，定址對象是反轉 map 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 map 中最後一個元素後面的位置 (未反轉 map 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 map 搭配使用，就如同 [end](#end) 是與 map 搭配使用一樣。

如果將 `rend` 的傳回值指派給 `const_reverse_iterator`，便無法修改 map 物件。 如果將 `rend` 的傳回值指派給 `reverse_iterator`，則可以修改 map 物件。

`rend` 可以用來測試反轉迭代器是否已到達其 map 的結尾。

`rend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>reverse_iterator

一種類型，提供可讀取或修改反轉 map 中元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 map。

由`reverse_iterator`對應定義的會指向專案, 這些專案是[value_type](#value_type)的物件 (其為`pair<const Key, Type>`類型), 其第一個成員是專案的索引鍵, 而第二個成員是元素所持有的對應基準。

若要對`reverse_iterator`指向`->`對應中某個元素的*rIter*取值, 請使用運算子。

若要存取該元素的索引鍵值，請使用 `rIter` -> **first**，這等同於 (\* `rIter`). **first**。 若要存取該元素的已對應資料值，請使用 `rIter` -> **second**，這等同於 (\* `rIter`). **first**。

### <a name="example"></a>範例

如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#rbegin) 的範例。

## <a name="size"></a>容量

傳回對應中項目的數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

地圖目前的長度。

### <a name="example"></a>範例

下列範例示範 map::size 成員函式的用法。

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>size_type

一種不帶正負號的整數類型，可代表 map 中的元素數目。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例。

## <a name="swap"></a>調換

交換兩個對應的項目。

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*再*\
提供要與目標 map 交換之元素的引數 map。

### <a name="remarks"></a>備註

任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 map 中，成員函式就不會使其失效。

### <a name="example"></a>範例

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>upper_bound

傳回迭代器，指向 map 中索引鍵值大於指定索引鍵值的第一個元素。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>參數

*擊鍵*\
要與所搜尋之對應中元素的排序鍵值比較的引數索引鍵值。

### <a name="return-value"></a>傳回值

`iterator` 或`const_iterator` , 定址對應中索引鍵大於引數索引鍵的元素位置, 或如果找不到與該索引鍵相符的專案, 則定址物件是 map 中最後一個元素後面的位置。

如果將傳回值指派給 `const_iterator`，便無法修改 map 物件。 如果將傳回值指派給`iterator`, 則可以修改 map 物件。

### <a name="example"></a>範例

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>value_comp

成員函式會傳回函式物件，此物件可藉由比較 map 中元素的索引鍵值來判斷這些元素的順序。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>傳回值

傳回 map 用來排序其元素的比較函式物件。

### <a name="remarks"></a>備註

對於 map *m*, 如果兩個專案*e1*(*版 k1*, *d1*) 和*e2*(*k2*, *d2*) 都是類型`value_type`的物件, 其中*版 k1*和*版 k1*是其類型`key_type`的索引鍵和*d1* ,*d2*是其類型`mapped_type`的資料, `m.value_comp(e1, e2)`而相當於`m.key_comp(k1, k2)`。 預存物件會定義成員函式

`bool operator( value_type& left, value_type& right);`

如果 `left` 的索引鍵值在前面且在排序次序中不等於 `right` 的索引鍵值，此函式就會傳回 **true**。

### <a name="example"></a>範例

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

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

   if(vc1( *pr2.first, *pr1.first ) == true )
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

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a> value_type

以元素形式儲存在 map 中的物件類型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>範例

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
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

## <a name="see-also"></a>另請參閱

[容器](../cpp/containers-modern-cpp.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
