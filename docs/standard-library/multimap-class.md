---
title: "multimap 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multimap
- std.multimap
- map/std::multimap
- std::multimap
dev_langs:
- C++
helpviewer_keywords:
- multimap class
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 1fa25ed3e958087a9fd602ac4e3914cc7a42edca
ms.lasthandoff: 02/24/2017

---
# <a name="multimap-class"></a>multimap 類別
「C++ 標準程式庫」multimap 類別可用來在集合中儲存及擷取資料，其中集合中的每個元素都成對，同時具有資料值和排序鍵。 索引鍵的值不需要是唯一的，用於自動排序資料。 多重對應中項目的值可以直接變更，但其關聯的索引鍵值不可以直接變更。 相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Key,   
    class Type,   
    class Traits=less <Key>,   
    class Allocator=allocator <pair  <const Key, Type>>>  
class multimap;  
```  
  
#### <a name="parameters"></a>參數  
 `Key`  
 要存放在多重對應中的索引鍵資料類型。  
  
 `Type`  
 要存放在多重對應中的項目資料類型。  
  
 `Traits`  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在多重對應中的相對順序。 二元述詞 `less<Key>` 是預設值。  
  
 在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關對應之記憶體配置和解除配置的詳細資訊。 這個引數是選擇性的，而且預設值是 `allocator<pair <const Key, Type> >`。  
  
## <a name="remarks"></a>備註  
 「C++ 標準程式庫」multimap 類別是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。  
  
-   多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目資料值。  
  
-   一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。  
  
-   樣板類別，因為它提供的功能是泛型，因此與做為項目或索引鍵包含的特定資料類型是獨立的。 用於項目或索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。  
  
 map 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#multimap__insert) 和 [multimap](#multimap__multimap) 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的一組需求，因此，使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通有關迭代器範圍 `[First, Last)`。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 關聯的容器已針對查閱、插入和移除作業最佳化。 明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，多重對應應該是首選的關聯容器。 這種結構的模型是已排序的關鍵字清單，其關聯的字串値 (例如) 提供定義，但不一定唯一定義文字。 如果關鍵字是唯一定義，因此索引鍵是唯一的，則對應是首選容器。 另一方面，如果只儲存文字清單，則集合是正確的容器。 如果允許文字的多個項目，則集合是適當的容器結構。  
  
 multimap 會藉由呼叫 [key_compare](#multimap__key_compare) 類型的預存函式物件，排序它所控制的序列。 這個預存物件是可藉由呼叫成員函式 [key_comp](#multimap__key_comp) 來存取的比較函式。 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 `f(x,y)` 是有兩個引數物件 `x` 和 `y` 以及傳回值 true 或 false 的函式物件。 如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 `x` 和 `y` 在 `f(x,y)` 和 `f(y,x)` 為 false 時定義為相等，則施加於集合的順序是嚴格弱式順序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。  
  
 在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
## <a name="members"></a>Members  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[multimap](#multimap__multimap)|建構一個空的 `multimap`，或是其他 `multimap` 的全部或部分複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#multimap__allocator_type)|類型，表示 `allocator` 物件的 `multimap` 類別。|  
|[const_iterator](#multimap__const_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的 `multimap` 項目。|  
|[const_pointer](#multimap__const_pointer)|類型，提供 `const` 中 `multimap` 項目之指標。|  
|[const_reference](#multimap__const_reference)|類型，提供儲存在 `const` 中供讀取和執行 `multimap` 作業之 `const` 項目的參考。|  
|[const_reverse_iterator](#multimap__const_reverse_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的任何 `multimap` 項目。|  
|[difference_type](#multimap__difference_type)|帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中 `multimap` 的項目數。|  
|[iterator](#multimap__iterator)|類型，提供兩個參考相同 `multimap` 內項目的迭代器之間的差異。|  
|[key_compare](#multimap__key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `multimap` 中的相對順序。|  
|[key_type](#multimap__key_type)|類型，描述構成 `multimap` 每個元素的排序鍵物件。|  
|[mapped_type](#multimap__mapped_type)|類型，表示儲存在 `multimap` 中的資料類型。|  
|[pointer](#multimap__pointer)|類型，提供 `const` 中 `multimap` 項目之指標。|  
|[reference](#multimap__reference)|類型，提供儲存在 `multimap` 中之項目的參考。|  
|[reverse_iterator](#multimap__reverse_iterator)|類型，提供可以讀取或修改反轉 `multimap` 中之項目的雙向迭代器。|  
|[size_type](#multimap__size_type)|不帶正負號的整數類型，提供 `const` 中 `multimap` 項目之指標。|  
|[value_type](#multimap__value_type)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `multimap` 中的相對順序。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[begin](#multimap__begin)|傳回迭代器，為 `multimap` 中的第一個項目定址。|  
|[cbegin](#multimap__cbegin)|傳回常數迭代器，為 `multimap` 中的第一個項目定址。|  
|[cend](#multimap__cend)|傳回常數迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|  
|[clear](#multimap__clear)|清除 `multimap` 的所有項目。|  
|[count](#multimap__count)|傳回 `multimap` 中索引鍵符合參數指定之索引鍵的項目數目。|  
|[crbegin](#multimap__crbegin)|傳回常數迭代器，為反轉 `multimap` 中的第一個項目定址。|  
|[crend](#multimap__crend)|傳回常數迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|  
|[emplace](#multimap__emplace)|將就地建構的項目插入 `multimap` 中。|  
|[emplace_hint](#multimap__emplace_hint)|將就地建構的項目 (含位置提示) 插入 `multimap` 中。|  
|[empty](#multimap__empty)|測試 `multimap` 是否為空白。|  
|[end](#multimap__end)|傳回迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|  
|[equal_range](#multimap__equal_range)|尋找項目索引鍵符合指定值的項目範圍。|  
|[erase](#multimap__erase)|從指定的位置移除 `multimap` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](#multimap__find)|傳回迭代器，定址 `multimap` 中索引鍵等於指定索引鍵之項目的第一個位置。|  
|[get_allocator](#multimap__get_allocator)|傳回用來建構 `allocator` 的 `multimap` 物件複本。|  
|[insert](#multimap__insert)|將項目或項目範圍插入至 `multimap`。|  
|[key_comp](#multimap__key_comp)|擷取 `multimap` 中用來排序索引鍵的比較物件之複本。|  
|[lower_bound](#multimap__lower_bound)|傳回迭代器，指向 `multimap` 中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max_size](#multimap__max_size)|傳回 `multimap` 的最大長度。|  
|[rbegin](#multimap__rbegin)|傳回迭代器，為反轉 `multimap` 中的第一個項目定址。|  
|[rend](#multimap__rend)|傳回迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|  
|[size](#multimap__size)|傳回 `multimap` 中項目的數目。|  
|[swap](#multimap__swap)|交換兩個 `multimap` 的項目。|  
|[upper_bound](#multimap__upper_bound)|傳回迭代器，指向 `multimap` 中索引鍵大於特定索引鍵的第一個項目。|  
|[value_comp](#multimap__value_comp)|成員函式傳回函式物件，可藉由比較其索引鍵值判斷 `multimap` 中項目的順序。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator=](#multimap__operator_eq)|用另一個 `multimap` 的複本取代 `multimap` 的項目。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<map>  
  
 **命名空間：** std  
  
 ( **key**, **value**) 配對會以 `pair` 類型的物件形式儲存在 multimap 中。 pair 類別需要 \<utility> 標頭，而 \<map> 會自動包含此標頭。  
  
##  <a name="a-namemultimapallocatortypea--multimapallocatortype"></a><a name="multimap__allocator_type"></a>  multimap::allocator_type  
 一種類型，代表 multimap 物件的配置器類別。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="example"></a>範例  
  如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#multimap__get_allocator) 的範例。  
  
##  <a name="a-namemultimapbegina--multimapbegin"></a><a name="multimap__begin"></a>  multimap::begin  
 傳回迭代器，定址對象是 multimap 中的第一個元素。  
  
```  
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
  
##  <a name="a-namemultimapcbegina--multimapcbegin"></a><a name="multimap__cbegin"></a>  multimap::cbegin  
 傳回 `const` 迭代器，為範圍中的第一個項目定址。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 `const` 雙向存取迭代器，指向範圍的第一個項目，或指向空白範圍結尾 (空白範圍 `cbegin() == cend()`) 之外的位置。  
  
### <a name="remarks"></a>備註  
 傳回值為 `cbegin` 時，無法修改範圍中的項目。  
  
 您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將 `Container` 視為任何一種支援 `begin()` 和 `cbegin()` 的可修改 (非 `const`) 容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namemultimapcenda--multimapcend"></a><a name="multimap__cend"></a>  multimap::cend  
 傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 指向範圍結尾之外的 `const` 雙向存取迭代器。  
  
### <a name="remarks"></a>備註  
 `cend` 用來測試迭代器是否已超過其範圍結尾。  
  
 您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將 `Container` 視為支援 `end()` 和 `cend()` 且可修改的任何種類 (非 `const`) 容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 `cend` 所傳回的值不應該取值。  
  
##  <a name="a-namemultimapcleara--multimapclear"></a><a name="multimap__clear"></a>  multimap::clear  
 清除 multimap 的所有元素。  
  
```  
void clear();
```  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 multimap::clear 成員函式。  
  
```  
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
  
##  <a name="a-namemultimapconstiteratora--multimapconstiterator"></a><a name="multimap__const_iterator"></a>  multimap::const_iterator  
 一種類型，提供可讀取 multimap 中 **const** 元素的雙向迭代器。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_iterator` 無法用來修改元素的值。  
  
 multimap 所定義的 `const_iterator` 會指向 [value_type](#multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***const Key**, **Type***>*。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 若要對指向 multimap 中某個元素的 `const_iterator``cIter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `cIter` -> **first**，這等同於 (\* `cIter`). **first**。 若要存取該元素的已對應資料值，請使用 `cIter` -> **second**，這等同於 (\* `cIter`). **second**。  
  
### <a name="example"></a>範例  
  如需使用 `const_iterator` 的範例，請參閱 [begin](#multimap__begin) 的範例。  
  
##  <a name="a-namemultimapconstpointera--multimapconstpointer"></a><a name="multimap__const_pointer"></a>  multimap::const_pointer  
 一種類型，提供 multimap 中 **const** 元素的指標。  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_pointer` 無法用來修改元素的值。  
  
 在大多數情況下，應該使用 [iterator](#multimap__iterator) 來存取 multimap 物件中的元素。  
  
##  <a name="a-namemultimapconstreferencea--multimapconstreference"></a><a name="multimap__const_reference"></a>  multimap::const_reference  
 一種類型，提供對儲存在 multimap 中以供讀取和執行 **const** 運算之 **const** 元素的參考。  
  
```  
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
   // non-const_reference cannot be used to access the key  
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
  
##  <a name="a-namemultimapconstreverseiteratora--multimapconstreverseiterator"></a><a name="multimap__const_reverse_iterator"></a>  multimap::const_reverse_iterator  
 一種類型，提供可讀取 multimap 中任何 **const** 元素的雙向迭代器。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 multimap。  
  
 multimap 所定義的 `const_reverse_iterator` 會指向 [value_type](#multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***const Key**, **Type***>*。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 若要對指向 multimap 中某個元素的 `const_reverse_iterator``crIter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `crIter` -> **first**，這等同於 (\* `crIter`). **first**。 若要存取該元素的已對應資料值，請使用 `crIter` -> **second**，這等同於 (\* `crIter`). **first**。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#multimap__rend) 的範例。  
  
##  <a name="a-namemultimapcounta--multimapcount"></a><a name="multimap__count"></a>  multimap::count  
 傳回 multimap 中索引鍵符合參數指定之索引鍵的項目數。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要從 multimap 中比對之項目的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 排序索引鍵符合參數索引鍵的項目數。如果 multimap 不含具有相符索引鍵的項目則為 0。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回範圍中的項目數  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )  
  
 中索引鍵值為 ` key` 的項目數。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 multimap::count 成員函式。  
  
```  
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
  
    // Elements do not need to have unique keys in multimap,  
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
  
##  <a name="a-namemultimapcrbegina--multimapcrbegin"></a><a name="multimap__crbegin"></a>  multimap::crbegin  
 傳回常數迭代器，定址對象是反轉 multimap 中的第一個元素。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 [multimap](../standard-library/multimap-class.md) 中的第一個元素，或未反轉 `multimap` 中的最後一個元素。  
  
### <a name="remarks"></a>備註  
 `crbegin` 是與反轉 `multimap` 搭配使用，就如同 [begin](#multimap__begin) 是與 `multimap` 搭配使用一樣。  
  
 有 `crbegin` 的傳回值時，無法修改 `multimap` 物件。  
  
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
  
##  <a name="a-namemultimapcrenda--multimapcrend"></a><a name="multimap__crend"></a>  multimap::crend  
 傳回常數迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 [multimap](../standard-library/multimap-class.md) 中最後一個元素後面的位置 (未反轉 `multimap` 中第一個元素前面的位置)。  
  
### <a name="remarks"></a>備註  
 `crend` 是與反轉 `multimap` 搭配使用，就如同 [multimap::end](#multimap__end) 是與 `multimap` 搭配使用一樣。  
  
 有 `crend` 的傳回值時，無法修改 `multimap` 物件。  
  
 `crend` 可以用來測試反轉迭代器是否已到達其 `multimap` 的結尾。  
  
 `crend` 所傳回的值不應該取值。  
  
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
  
##  <a name="a-namemultimapdifferencetypea--multimapdifferencetype"></a><a name="multimap__difference_type"></a>  multimap::difference_type  
 一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 multimap 的元素數目。  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 `difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 ` first` 和 ` last` 之間範圍 *[ first,  last)* 內的元素數目，包括 ` first` 所指的元素以及上限到 *last* 所指元素 (但不包含此元素) 的元素範圍。  
  
 請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別，但只有隨機存取容器 (例如 vector) 所提供的隨機存取迭代器，才支援迭代器之間的減法。  
  
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
  
##  <a name="a-namemultimapemplacea--multimapemplace"></a><a name="multimap__emplace"></a>  multimap::emplace  
 插入就地建構 (未執行任何複製或移動作業) 的元素。  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`args`|轉送以建構要插入到 multimap 中之元素的引數。|  
  
### <a name="return-value"></a>傳回值  
 指向新插入之元素的迭代器。  
  
### <a name="remarks"></a>備註  
 此函式不會使任何對容器元素的參考無效，但可能會使指向容器的所有迭代器無效。  
  
 如果在插入時擲回例外狀況，就會將容器保持不變，並重新擲回例外狀況。  
  
 元素的 [value_type](../standard-library/map-class.md#map__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
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
  
##  <a name="a-namemultimapemplacehinta--multimapemplacehint"></a><a name="multimap__emplace_hint"></a>  multimap::emplace_hint  
 將就地建構 (未執行任何複製或移動作業) 的元素連同位置提示一起插入。  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`args`|轉送以建構要插入到 multimap 中之元素的引數。|  
|`where`|要開始搜尋正確的插入點的地方 (若該點緊接於 `where` 之前，則可能會在分攤常數時間插入，而不是對數時間)。|  
  
### <a name="return-value"></a>傳回值  
 指向新插入之元素的迭代器。  
  
### <a name="remarks"></a>備註  
 此函式不會使任何對容器元素的參考無效，但可能會使指向容器的所有迭代器無效。  
  
 在定位期間，如果擲回例外狀況，則不會修改容器的狀態。  
  
 元素的 [value_type](../standard-library/map-class.md#map__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 如需程式碼範例，請參閱 [map::emplace_hint](../standard-library/map-class.md#map__emplace_hint)。  
  
##  <a name="a-namemultimapemptya--multimapempty"></a><a name="multimap__empty"></a>  multimap::empty  
 測試 multimap 是否是空的。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 multimap 是空的，即為 **true**；如果 multimap 不是空的，則為 **false**。  
  
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
  
##  <a name="a-namemultimapenda--multimapend"></a><a name="multimap__end"></a>  multimap::end  
 傳回超出結尾 (past-the-end) 迭代器。  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>傳回值  
 超出結尾迭代器。 如果 multimap 是空的，則 `multimap::end() == multimap::begin()`。  
  
### <a name="remarks"></a>備註  
 **end** 是用來測試迭代器是否已超過其 multimap 的結尾。  
  
 **end** 所傳回的值不應該被取值。  
  
 如需程式碼範例，請參閱 [multimap::find](#multimap__find)。  
  
##  <a name="a-namemultimapequalrangea--multimapequalrange"></a><a name="multimap__equal_range"></a>  multimap::equal_range  
 尋找項目索引鍵符合指定值的項目範圍。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 一組迭代器，其中第一個是索引鍵的 [lower_bound](#multimap__lower_bound)，第二個是索引鍵的 [upper_bound](#multimap__upper_bound)。  
  
 若要存取成員函式所傳回之配對 `pr` 的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之配對 `pr` 的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。  
  
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
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
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
  
##  <a name="a-namemultimaperasea--multimaperase"></a><a name="multimap__erase"></a>  multimap::erase  
 從 multimap 中指定的位置移除某個元素或某個範圍的元素，或移除符合指定索引鍵的元素。  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>參數  
 `Where`  
 要移除之項目的位置。  
  
 `First`  
 要移除之第一個項目的位置。  
  
 `Last`  
 緊接在要移除之最後一個元素後面的位置。  
  
 `Key`  
 要移除之元素的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 針對前兩個成員函式，會傳回雙向迭代器，其中指定任何移除之元素後剩餘的第一個元素，或如果沒有這類元素，則傳回 map 結尾的元素。  
  
 針對第三個成員函式，會傳回已從 multimap 移除的元素數目。  
  
### <a name="remarks"></a>備註  
 如需程式碼範例，請參閱 [map::erase](../standard-library/map-class.md#map__erase)。  
  
##  <a name="a-namemultimapfinda--multimapfind"></a><a name="multimap__find"></a>  multimap::find  
 傳回迭代器，其指向 multimap 中索引鍵等於指定索引鍵的第一個元素的位置。  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要以所搜尋之 multimap 中元素的排序鍵比對的索引鍵值。  
  
### <a name="return-value"></a>傳回值  
 迭代器，參考對象是具有指定索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，則是 multimap 中最後一個元素後面的位置 ( `multimap::end()`)。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回迭代器，其表示 multimap 中排序鍵 (在二元述詞下根據較少的比較性關聯引發排序) 等於引數索引鍵的元素。  
  
 如果將 **find** 的傳回值指派給 **const_iterator**，便無法修改 multimap 物件。 如果將 **find** 的傳回值指派給 **iterator**，則可以修改 multimap 物件。  
  
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
  
##  <a name="a-namemultimapgetallocatora--multimapgetallocator"></a><a name="multimap__get_allocator"></a>  multimap::get_allocator  
 傳回一份用來建構 multimap 的配置器物件複本。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 multimap 所使用的配置器。  
  
### <a name="remarks"></a>備註  
 multimap 類別的配置器會指定此類別管理儲存體的方式。 「C++ 標準程式庫」容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。  
  
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
  
##  <a name="a-namemultimapinserta--multimapinsert"></a><a name="multimap__insert"></a>  multimap::insert  
 將某個元素或元素範圍插入 multimap 中。  
  
```  
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
  
|||  
|-|-|  
|參數|描述|  
|`Val`|要插入至 multimap 的元素值。|  
|`Where`|要開始搜尋正確的插入點的地方 (若該點緊接於 `Where` 之前，則可能會在分攤常數時間插入，而不是對數時間)。|  
|`ValTy`|範本參數，可指定 map 可用來建構 [value_type](../standard-library/map-class.md#map__value_type) 之元素的引數類型，並將 `Val` 以引數形式完整轉送。|  
|`First`|要複製之第一個元素的位置。|  
|`Last`|要複製之最一個元素後方的位置。|  
|`InputIterator`|符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#map__value_type) 物件的類型。|  
|`IList`|要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>傳回值  
 單一元素插入成員函式 (1) 和 (2)，會將迭代器傳回至在 multimap 中插入新元素的位置。  
  
 具有提示的單一元素成員函式 (3) 和 (4)，會傳回迭代器，其指向在 multimap 中插入新元素的位置。  
  
### <a name="remarks"></a>備註  
 此函式不會使指標或參考無效，但是可能會使容器的所有迭代器無效。  
  
 在只插入一個元素的期間，若擲出例外狀況，則不會修改容器的狀態。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。  
  
 容器的 [value_type](../standard-library/map-class.md#map__value_type) 是屬於容器的 typedef，而就 map 而言，`multimap<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 範圍成員函式 (5) 會將元素值序列插入 multimap，而 multimap 對應至範圍 `[First, Last)` 中迭代器指定的每個元素；因此不會插入 `Last`。 容器成員函式 `end()` 是指容器中最後一個元素後方的位置；例如，陳述式 `m.insert(v.begin(), v.end());` 會將 `v` 的所有元素插入至 `m`。  
  
 初始設定式清單成員函式 (6) 會使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 map。  
  
 針對插入就地建構 (也就是未執行任何複製或移動作業) 的元素，請參閱 [multimap::emplace](#multimap__emplace) 和 [multimap::emplace_hint](#multimap__emplace_hint)。  
  
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
  
##  <a name="a-namemultimapiteratora--multimapiterator"></a><a name="multimap__iterator"></a>  multimap::iterator  
 一種類型，提供可讀取或修改 multimap 中任何元素的雙向迭代器。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>備註  
 multimap 所定義的 **iterator** 會指向 [value_type](#multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***const Key**, **Type***>*。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 若要對指向 multimap 中某個元素的 **iterator**`Iter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `Iter` -> **first**，這等同於 (\* `Iter`). **first**。 若要存取該元素的已對應資料值，請使用 `Iter` -> **second**，這等同於 (\* `Iter`). **second**。  
  
 類型 **iterator** 可用來修改元素的值。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 **iterator** 的範例，請參閱 [begin](#multimap__begin) 的範例。  
  
##  <a name="a-namemultimapkeycompa--multimapkeycomp"></a><a name="multimap__key_comp"></a>  multimap::key_comp  
 擷取一份用來排序 multimap 中索引鍵的比較物件複本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 multimap 用來排序其元素的函式物件。  
  
### <a name="remarks"></a>備註  
 預存物件會定義成員函式  
  
 **bool operator**( **const Key&** *x*, **const Key&** *y*);  
  
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
  
##  <a name="a-namemultimapkeycomparea--multimapkeycompare"></a><a name="multimap__key_compare"></a>  multimap::key_compare  
 一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷 multimap 中兩個元素的相對順序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>備註  
 **key_compare** 與範本參數 `Traits` 同義。  
  
 如需有關 `Traits` 的詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)主題。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#multimap__key_comp) 的範例。  
  
##  <a name="a-namemultimapkeytypea--multimapkeytype"></a><a name="multimap__key_type"></a>  multimap::key_type  
 一種類型，描述構成 multimap 每個元素的排序鍵物件。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 **key_type** 與範本參數 `Key` 同義。  
  
 如需有關 `Key` 的詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)主題的＜備註＞一節。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#multimap__value_type) 的範例。  
  
##  <a name="a-namemultimaplowerbounda--multimaplowerbound"></a><a name="multimap__lower_bound"></a>  multimap::lower_bound  
 傳回迭代器，指向 multimap 中索引鍵等於或大於指定索引鍵的第一個元素。  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 iterator 或 `const_iterator`，定址對象是 multimap 中索引鍵等於或大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 multimap 中最後一個元素後面的位置。  
  
 如果將 `lower_bound` 的傳回值指派給 `const_iterator`，便無法修改 multimap 物件。 如果將 `lower_bound` 的傳回值指派給 **iterator**，則可以修改 multimap 物件。  
  
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
  
##  <a name="a-namemultimapmappedtypea--multimapmappedtype"></a><a name="multimap__mapped_type"></a>  multimap::mapped_type  
 一種類型，代表儲存在 multimap 中的資料類型。  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>備註  
 `mapped_type` 與範本參數 `Type` 同義。  
  
 如需有關 `Type` 的詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)主題。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#multimap__value_type) 的範例。  
  
##  <a name="a-namemultimapmaxsizea--multimapmaxsize"></a><a name="multimap__max_size"></a>  multimap::max_size  
 傳回 multimap 的最大長度。  
  
```  
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
  
##  <a name="a-namemultimapmultimapa--multimapmultimap"></a><a name="multimap__multimap"></a>  multimap::multimap  
 建構一個空的 multimap，或是某個其他 multimap 之全部或部分複本的 multimap。  
  
```  
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
  
|||  
|-|-|  
|參數|說明|  
|`Al`|要用於此 multimap 物件的儲存體配置器類別，預設為 Allocator。|  
|`Comp`|類型為 **constTraits** 並用來排序 map 中元素的比較函式，預設為 **Traits**。|  
|`Right`|要從中複製所建構之集合的對應。|  
|`First`|要複製的元素範圍中第一個元素的位置。|  
|`Last`|超出要複製之元素範圍的第一個元素的位置。|  
|`IList`|從中複製項目的 initializer_list。|  
  
### <a name="remarks"></a>備註  
 所有建構函式都會儲存一種配置器物件，此物件可管理 multimap 的記憶體儲存，且之後藉由呼叫 [get_allocator](#multimap__get_allocator) 即可傳回此物件。 在類別宣告中經常會省略 allocator 參數，而前處理巨集會用來取代替代配置器。  
  
 所有建構函式都會將其 multimap 初始化。  
  
 所有建構函式都會儲存一個 `Traits` 類型的函式物件，此物件可用來在 multimap 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#multimap__key_comp) 即可傳回此物件。  
  
 前三個建構函式會指定空的初始 multimap，第二個建構函式會指定建立元素順序時所要使用的比較函式類型 ( `Comp`)，而第三個建構函式則會明確指定所要使用的配置器類型 ( `Al`)。 關鍵字 `explicit` 會隱藏某些類型的自動類型轉換。  
  
 第四個建構函式會指定 multimap `Right` 的複本。  
  
 第五個建構函式會藉由移動 `Right` 來指定 multimap 的複本。  
  
 第六、第七及第八個建構函式會複製 initializer_list 的成員。  
  
 接下來的三個建構函式會複製 map 的範圍 `[First, Last)`，其中會以越來越明確的方式指定類別 **Traits** 的比較函式及配置器的類型。  
  
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
    // function of geater than, then insert 2 elements  
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
  
##  <a name="a-namemultimapoperatoreqa--multimapoperator"></a><a name="multimap__operator_eq"></a>  multimap::operator=  
 將 multimap 的元素以另一個 multimap 的複本取代。  
  
```  
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` right`|要複製到 `multimap` 中的 [multimap](../standard-library/multimap-class.md)。|  
  
### <a name="remarks"></a>備註  
 清除 `multimap` 中的任何現有項目之後，`operator=` 會將 ` right` 的內容複製或移到 `multimap` 中。  
  
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
  
##  <a name="a-namemultimappointera--multimappointer"></a><a name="multimap__pointer"></a>  multimap::pointer  
 一種類型，提供 multimap 中元素的指標。  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 **pointer** 可用來修改元素的值。  
  
 在大多數情況下，應該使用 [iterator](#multimap__iterator) 來存取 multimap 物件中的元素。  
  
##  <a name="a-namemultimaprbegina--multimaprbegin"></a><a name="multimap__rbegin"></a>  multimap::rbegin  
 傳回迭代器，定址對象是反轉 multimap 中的第一個元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 multimap 中的第一個元素，或未反轉 multimap 中的最後一個元素。  
  
### <a name="remarks"></a>備註  
 `rbegin` 是與反轉 multimap 搭配使用，就如同 [begin](#multimap__begin) 是與 multimap 搭配使用一樣。  
  
 如果將 `rbegin` 的傳回值指派給 `const_reverse_iterator`，便無法修改 multimap 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改 multimap 物件。  
  
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
   // throught a multimap in a forward order  
   cout << "The multimap is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a multimap in a reverse order  
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
  
##  <a name="a-namemultimapreferencea--multimapreference"></a><a name="multimap__reference"></a>  multimap::reference  
 一種類型，提供對儲存在 multimap 中元素的參考。  
  
```  
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
   // non-const_reference cannot be used to access the key  
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
  
##  <a name="a-namemultimaprenda--multimaprend"></a><a name="multimap__rend"></a>  multimap::rend  
 傳回迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 multimap 中最後一個元素後面的位置 (未反轉 multimap 中第一個元素前面的位置)。  
  
### <a name="remarks"></a>備註  
 `rend` 是與反轉 multimap 搭配使用，就如同 [end](../standard-library/map-class.md#map__end) 是與 multimap 搭配使用一樣。  
  
 如果將 `rend` 的傳回值指派給 `const_reverse_iterator`，便無法修改 multimap 物件。 如果將 `rend` 的傳回值指派給 `reverse_iterator`，則可以修改 multimap 物件。  
  
 `rend` 可以用來測試反轉迭代器是否已到達其 multimap 的結尾。  
  
 `rend` 所傳回的值不應該取值。  
  
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
   // throught a multimap in a forward order  
   cout << "The multimap is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a multimap in a reverse order  
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
  
##  <a name="a-namemultimapreverseiteratora--multimapreverseiterator"></a><a name="multimap__reverse_iterator"></a>  multimap::reverse_iterator  
 一種類型，提供可讀取或修改反轉 multimap 中元素的雙向迭代器。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `reverse_iterator` 是用來反向逐一查看 multimap。  
  
 multimap 所定義的 `reverse_iterator` 會指向 [value_type](#multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***const Key**, **Type***>*。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 若要對指向 multimap 中某個元素的 `reverse_iterator``rIter` 進行取值，請使用 -> 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `rIter` -> **first**，這等同於 (\* `rIter`). **first**。 若要存取該元素的已對應資料值，請使用 `rIter` -> **second**，這等同於 (\* `rIter`). **first**。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#multimap__rbegin) 的範例。  
  
##  <a name="a-namemultimapsizea--multimapsize"></a><a name="multimap__size"></a>  multimap::size  
 傳回 multimap 中的項目數目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 multimap 的目前長度。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 multimap::size 成員函式。  
  
```  
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
  
##  <a name="a-namemultimapsizetypea--multimapsizetype"></a><a name="multimap__size_type"></a>  multimap::size_type  
 一種不帶正負號的整數類型，可計算 multimap 中的元素數目。  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#multimap__size) 的範例。  
  
##  <a name="a-namemultimapswapa--multimapswap"></a><a name="multimap__swap"></a>  multimap::swap  
 交換兩個 multimap 的元素。  
  
```  
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供要交換之元素的 multimap，或要與 multimap ` left` 交換元素的 multimap。  
  
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
  
##  <a name="a-namemultimapupperbounda--multimapupperbound"></a><a name="multimap__upper_bound"></a>  multimap::upper_bound  
 傳回迭代器，指向 multimap 中索引鍵大於指定索引鍵的第一個元素。  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 iterator 或 `const_iterator`，定址對象是 multimap 中索引鍵大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 multimap 中最後一個元素後面的位置。  
  
 如果將傳回值指派給 `const_iterator`，便無法修改 multimap 物件。 如果將傳回值指派給 **iterator**，則可以修改 multimap 物件。  
  
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
   // found using a derefenced iterator addressing the location  
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
  
##  <a name="a-namemultimapvaluecompa--multimapvaluecomp"></a><a name="multimap__value_comp"></a>  multimap::value_comp  
 成員函式會傳回函式物件，此物件可藉由比較 multimap 中元素的索引鍵值來判斷這些元素的順序。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 multimap 用來排序其元素的比較函式物件。  
  
### <a name="remarks"></a>備註  
 就 multimap *m* 而言，如果兩個元素 *e*1( *k*1, *d*1) 和 *e*2( *k*2, `d`2) 是 `value_type` 類型的物件，其中 *k*1 和 *k*2 是其 `key_type` 類型的索引鍵，而 `d`1 和 `d`2 是其 `mapped_type` 類型的資料，則 *m.*`value_comp`( *e*1, *e*2) 會等於 *m.*`key_comp`( *k*1, *k*2)。  
  
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
  
##  <a name="a-namemultimapvaluetypea--multimapvaluetype"></a><a name="multimap__value_type"></a>  multimap::value_type  
 一種類型，代表以元素形式儲存在 map 中的物件類型。  
  
```  
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
   // explicitely to avoid implicit type conversion  
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
 [\<map> 成員](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


