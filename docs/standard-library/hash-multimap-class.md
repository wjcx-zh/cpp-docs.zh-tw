---
title: "hash_multimap 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::hash_multimap
- stdext.hash_multimap
- hash_map/stdext::hash_multimap
- hash_multimap
- std::hash_multimap
- std.hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
caps.latest.revision: 24
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 4798371a8b27107de850d2b5de3cacc2713cae8e
ms.lasthandoff: 02/24/2017

---
# <a name="hashmultimap-class"></a>hash_multimap 類別
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 容器類別 hash_multimap 是「C++ 標準程式庫」的擴充功能，可用來在集合中儲存及快速擷取資料，其中集合中的每個元素都成對，具有排序鍵 (其值不需要是唯一的) 和關聯的資料值。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Key,   
    class Type,   
    class Traits=hash_compare <Key, less <Key>>,   
    class Allocator=allocator <pair  <const Key, Type>>>  
class hash_multimap  
```  
  
#### <a name="parameters"></a>參數  
 `Key`  
 要存放在 hash_multimap 中的索引鍵資料類型。  
  
 `Type`  
 要存放在 hash_multimap 中的項目資料類型。  
  
 `Traits`  
 包含兩個函式物件的類型：一個是屬於 `Traits` 類別 (能夠將兩個元素值以排序索引鍵做比較來判斷其相對順序)；一個是雜湊函式 (此為一元述詞，可將元素的索引鍵值對應到 **size_t** 類型的不帶正負號整數)。 這個引數是選用引數，且預設值是 `hash_compare``<Key, less<Key> >`。  
  
 `Allocator`  
 代表預存配置器物件的類型，其可封裝有關 hash_multimap 之記憶體配置與解除配置的詳細資訊。 這個引數是選用引數，且預設值是 `allocator<pair <const Key, Type> >`。  
  
## <a name="remarks"></a>備註  
 hash_multimap 是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已經過雜湊處理，因為其項目會依據套用至該項目索引鍵值之雜湊函式的值，分組到不同值區。  
  
-   多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目資料值。  
  
-   成對且相關聯的容器，因為其項目值與其索引鍵值不同。  
  
-   樣板類別，因為它提供的功能是泛型，因此與做為項目或索引鍵包含的特定資料類型是獨立的。 用於項目或索引鍵的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。  
  
 透過排序進行雜湊的主要優點是效率更佳；成功的雜湊能執行插入、刪除，相較於和排序技術容器中項目數目對數值成比例的時間，它會以常數平均時間進行搜尋。 hash_multimap 中項目的值可以直接變更，但相關聯的索引鍵值不可以直接變更。 相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 經過雜湊處理的相關聯容器，已針對查閱、插入及移除作業進行過最佳化。 搭配設計良好的雜湊函式使用時，明確支援這些作業的成員函式，效率相當良好，其會以平均而言為常數的時間執行作業，而與此容器中的項目數目無關。 設計良好的雜湊函式會產生雜湊值的均勻分佈，並盡可能減少衝突發生，當相異索引鍵值對應到相同的雜湊值時，就會發生所謂的衝突。 使用最糟的雜湊函式的最壞情況下，作業數目與序列中的項目數目成正比 (線性時間)。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，hash_multimap 應該要當成首選的相關聯容器。 這種結構的模型是已排序的關鍵字清單，其關聯的字串値 (例如) 提供定義，但不一定唯一定義文字。 如果以不重複的方式定義了關鍵字，而讓索引鍵沒有重複，則 hash_map 會是首選容器。 另一方面，如果只儲存了文字清單，則 hash_set 會是正確的容器。 如果允許出現多次文字，則 hash_multiset 即是適當的容器結構。  
  
 hash_multimap 會藉由呼叫 [value_compare](../standard-library/value-compare-class.md) 類型的預存雜湊 `Traits` 物件，排序它所控制的序列。 藉由呼叫成員函式 [key_comp](../standard-library/hash-map-class.md#hash_map__key_comp)，即可存取這個預存物件。 這類函式物件的行為必須與 [hash_compare](../standard-library/hash-compare-class.md)`<Key,  less<Key> >` 類別的物件相同。 尤其是針對 `Key` 類型的所有 `Key` 值，呼叫 `Traits (Key)` 會產生 `size_t` 類型值的分佈。  
  
 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等項目之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 f(x, y) 是有兩個引數物件 `x` 和 `y` 以及傳回值 `true` 或 `false` 的函式物件。 如果二元述詞並非其反身、非對稱且可轉移，而且如果同等項目可以轉移，其中兩個物件 `x` 和 `y` 在 f(x, y) 和 f(y, x) 為 `false` 時定義為同等項目等，則施加於 hash_multimap 的順序是嚴格弱式排序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。  
  
 受控制序列中實際的項目順序取決於雜湊函式、排序函式以及儲存於此容器物件中雜湊資料表目前的大小。 您無法判斷目前雜湊資料表的大小，因此一般而言，無法預測受控制序列中項目的順序。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 hash_multimap 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#hash_multimap__insert) 和 [hash_multimap](#hash_multimap__hash_multimap) 擁有以較弱的輸入迭代器作為範本參數的版本，其功能需求比雙向迭代器的類別所保證的還要少。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的 hash_multimap 需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是最基本的 hash_multimap 功能，但足以在成員函式的內容中，有意義地溝通有關迭代器 `[First, Last)` 的範圍。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[hash_multimap](#hash_multimap__hash_multimap)|建構特定大小的清單，或具有特定值之項目的清單，或具有特定 `allocator` 的清單，或是做為一些其他 `hash_multimap` 的複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#hash_multimap__allocator_type)|類型，表示 `allocator` 物件的 `hash_multimap` 類別。|  
|[const_iterator](#hash_multimap__const_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的 `hash_multimap` 項目。|  
|[const_pointer](#hash_multimap__const_pointer)|類型，提供 `const` 中 `hash_multimap` 項目之指標。|  
|[const_reference](#hash_multimap__const_reference)|類型，提供儲存在 `const` 中供讀取和執行 `hash_multimap` 作業之 `const` 項目的參考。|  
|[const_reverse_iterator](#hash_multimap__const_reverse_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的任何 `hash_multimap` 項目。|  
|[difference_type](#hash_multimap__difference_type)|帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中 `hash_multimap` 的項目數。|  
|[iterator](#hash_multimap__iterator)|類型，其提供可讀取或修改 `hash_multimap` 中任何項目的雙向迭代器。|  
|[key_compare](#hash_multimap__key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `hash_multimap` 中的相對順序。|  
|[key_type](#hash_multimap__key_type)|類型，描述構成 `hash_multimap` 每個元素的排序鍵物件。|  
|[mapped_type](#hash_multimap__mapped_type)|類型，表示儲存在 `hash_multimap` 中的資料類型。|  
|[pointer](#hash_multimap__pointer)|類型，其提供 `hash_multimap` 中項目的指標。|  
|[reference](#hash_multimap__reference)|類型，提供儲存在 `hash_multimap` 中之項目的參考。|  
|[reverse_iterator](#hash_multimap__reverse_iterator)|類型，提供可以讀取或修改反轉 `hash_multimap` 中之項目的雙向迭代器。|  
|[size_type](#hash_multimap__size_type)|不帶正負號的整數類型，可以表示 `hash_multimap` 中的項目數。|  
|[value_type](#hash_multimap__value_type)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `hash_multimap` 中的相對順序。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[begin](#hash_multimap__begin)|傳回迭代器，為 `hash_multimap` 中的第一個項目定址。|  
|[hash_multimap::cbegin](#hash_multimap__cbegin)|傳回常數迭代器，為 `hash_multimap` 中的第一個項目定址。|  
|[hash_multimap::cend](#hash_multimap__cend)|傳回常數迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[clear](#hash_multimap__clear)|清除 `hash_multimap` 的所有項目。|  
|[count](#hash_multimap__count)|傳回 `hash_multimap` 中索引鍵符合參數指定之索引鍵的項目數目。|  
|[hash_multimap::crbegin](#hash_multimap__crbegin)|傳回常數迭代器，為反轉 `hash_multimap` 中的第一個項目定址。|  
|[hash_multimap::crend](#hash_multimap__crend)|傳回常數迭代器，為反轉 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[hash_multimap::emplace](#hash_multimap__emplace)|將就地建構的項目插入 `hash_multimap` 中。|  
|[hash_multimap::emplace_hint](#hash_multimap__emplace_hint)|將就地建構的項目 (含位置提示) 插入 `hash_multimap` 中。|  
|[empty](#hash_multimap__empty)|測試 `hash_multimap` 是否為空白。|  
|[end](#hash_multimap__end)|傳回迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[equal_range](#hash_multimap__equal_range)|傳回迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[erase](#hash_multimap__erase)|從指定位置移除在 `hash_multimap` 中的項目或某個範圍的項目。|  
|[find](#hash_multimap__find)|傳回迭代器，為 `hash_multimap` 中索引鍵等於指定索引鍵項目位置定址。|  
|[get_allocator](#hash_multimap__get_allocator)|傳回用來建構 `allocator` 的 `hash_multimap` 物件複本。|  
|[insert](#hash_multimap__insert)|在 `hash_multimap` 中的指定位置插入項目或某個範圍的項目。|  
|[key_comp](#hash_multimap__key_comp)|擷取 `hash_multimap` 中用來排序索引鍵的比較物件之複本。|  
|[lower_bound](#hash_multimap__lower_bound)|傳回迭代器，其指向 `hash_multimap` 中索引鍵值等於或大於特定索引鍵值的第一個項目。|  
|[max_size](#hash_multimap__max_size)|傳回 `hash_multimap` 的最大長度。|  
|[rbegin](#hash_multimap__rbegin)|傳回迭代器，為反轉 `hash_multimap` 中的第一個項目定址。|  
|[rend](#hash_multimap__rend)|傳回迭代器，為反轉 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[size](#hash_multimap__size)|指定 `hash_multimap` 的新大小。|  
|[swap](#hash_multimap__swap)|交換兩個 `hash_multimap` 的項目。|  
|[upper_bound](#hash_multimap__upper_bound)|傳回迭代器，其會指向 `hash_multimap` 中索引鍵值大於特定索引鍵值的第一個項目。|  
|[value_comp](#hash_multimap__value_comp)|擷取 `hash_multimap` 中用於排序項目值之比較物件的複本。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[hash_multimap::operator=](#hash_multimap__operator_eq)|用另一個 `hash_multimap` 的複本取代 `hash_multimap` 的項目。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<hash_map>  
  
 **命名空間：** stdext  
  
##  <a name="a-namehashmultimapallocatortypea--hashmultimapallocatortype"></a><a name="hash_multimap__allocator_type"></a>  hash_multimap::allocator_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，代表 hash_multimap 物件的配置器類別。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 `allocator_type` 與範本參數 `Allocator` 同義。  
  
 如需有關 `Allocator` 的詳細資訊，請參閱 [hash_multimap 類別](../standard-library/hash-multimap-class.md)主題的＜備註＞一節。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#hash_multimap__get_allocator) 的範例。  
  
##  <a name="a-namehashmultimapbegina--hashmultimapbegin"></a><a name="hash_multimap__begin"></a>  hash_multimap::begin  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，定址對象是 hash_multimap 中的第一個元素。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>傳回值  
 雙向迭代器，定址對象是 hash_multimap 中的第一個元素，或空 hash_multimap 後面的位置。  
  
### <a name="remarks"></a>備註  
 如果將 **begin** 的傳回值指派給 `const_iterator`，便無法修改 hash_multimap 物件中的元素。 如果將 **begin** 的傳回值指派給 **iterator**，則可以修改 hash_multimap 物件中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_begin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 0, 0 ) );  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.begin ( );  
   cout << "The first element of hm1 is " << hm1_cIter -> first   
        << "." << endl;  
  
   hm1_Iter = hm1.begin ( );  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.begin ( );  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.begin( );  
   cout << "The first element of hm1 is now " << hm1_cIter -> first   
        << "." << endl;  
}  
```  
  
```Output  
The first element of hm1 is 0.  
The first element of hm1 is now 1.  
```  
  
##  <a name="a-namehashmultimapcbegina--hashmultimapcbegin"></a><a name="hash_multimap__cbegin"></a>  hash_multimap::cbegin  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回常數迭代器，定址對象是 hash_multimap 中的第一個元素。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數雙向迭代器，定址對象是 [hash_multimap](../standard-library/hash-multimap-class.md) 中的第一個元素，或空 `hash_multimap` 後面的位置。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_cbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="a-namehashmultimapcenda--hashmultimapcend"></a><a name="hash_multimap__cend"></a>  hash_multimap::cend  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回常數迭代器，定址對象是 hash_multimap 中最後一個元素後面的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數雙向迭代器，定址對象是 [hash_multimap](../standard-library/hash-multimap-class.md) 中最後一個元素後面的位置。 如果 `hash_multimap` 是空的，則 `hash_multimap::cend == hash_multimap::begin`。  
  
### <a name="remarks"></a>備註  
 `cend` 是用來測試迭代器是否已到達其 hash_multimap 的結尾。  
  
 `cend` 所傳回的值不應該取值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_cend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="a-namehashmultimapcleara--hashmultimapclear"></a><a name="hash_multimap__clear"></a>  hash_multimap::clear  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 清除 hash_multimap 的所有項目。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 hash_multimap::clear 成員函式。  
  
```  
// hash_multimap_clear.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 4));  
  
    i = hm1.size();  
    cout << "The size of the hash_multimap is initially "  
         << i  << "." << endl;  
  
    hm1.clear();  
    i = hm1.size();  
    cout << "The size of the hash_multimap after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the hash_multimap is initially 2.  
The size of the hash_multimap after clearing is 0.  
```  
  
##  <a name="a-namehashmultimapconstiteratora--hashmultimapconstiterator"></a><a name="hash_multimap__const_iterator"></a>  hash_multimap::const_iterator  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供可讀取 hash_multimap 中 **const** 元素的雙向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_iterator` 無法用來修改元素的值。  
  
 hash_multimap 所定義的 `const_iterator` 會指向 [value_type](#hash_multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***constKey, Type***>*。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 若要對指向 hash_multimap 中某個元素的 `const_iterator``cIter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `cIter` -> **first**，這等同於 (\* `cIter`). **first**。 若要存取該元素的已對應資料值，請使用 `cIter` -> **second**，這等同於 (\* `cIter`). **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需使用 `const_iterator` 的範例，請參閱 [begin](#hash_multimap__begin) 的範例。  
  
##  <a name="a-namehashmultimapconstpointera--hashmultimapconstpointer"></a><a name="hash_multimap__const_pointer"></a>  hash_multimap::const_pointer  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供 hash_multimap 中 **const** 元素的指標。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_pointer` 無法用來修改元素的值。  
  
 在大多數情況下，應該使用 [iterator](#hash_multimap__iterator) 來存取 hash_multimap 物件中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
##  <a name="a-namehashmultimapconstreferencea--hashmultimapconstreference"></a><a name="hash_multimap__const_reference"></a>  hash_multimap::const_reference  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供對儲存在 hash_multimap 中以供讀取和執行 **const** 運算之 **const** 元素的參考。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_const_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin() -> second );  
  
   cout << "The data value of 1st element in the hash_multimap is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of 1st element in the hash_multimap is 10.  
```  
  
##  <a name="a-namehashmultimapconstreverseiteratora--hashmultimapconstreverseiterator"></a><a name="hash_multimap__const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供可讀取 hash_multimap 中任何 **const** 元素的雙向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看 hash_multimap。  
  
 hash_multimap 所定義的 `const_reverse_iterator` 會指向 [value_type](#hash_multimap__value_type) 的物件，value_type 的類型為 `pair`*\<***const Key, Type>**，其第一個成員是元素的索引鍵，而第二個成員是該元素所持有的已對應資料。  
  
 若要對指向 hash_multimap 中某個元素的 `const_reverse_iterator``crIter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `crIter` -> **first**，這等同於 (\* `crIter`). **first**。 若要存取該元素的已對應資料值，請使用 `crIter` -> **second**，這等同於 (\* `crIter`). **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#hash_multimap__rend) 的範例。  
  
##  <a name="a-namehashmultimapcounta--hashmultimapcount"></a><a name="hash_multimap__count"></a>  hash_multimap::count  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回 hash_multimap 中索引鍵符合參數指定之索引鍵的項目數目。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要從 hash_multimap 中比對之項目的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果 hash_multimap 包含排序索引鍵符合參數索引鍵的項目則為 1；如果 hash_multimap 不含具有相符索引鍵的項目則為 0。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回範圍中的項目數  
  
 **[lower_bound (** ` key` **), upper_bound (** ` key` **) )**  
  
 其有索引鍵值 ` key`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 hash_multimap::count 成員函式。  
  
```  
// hash_multimap_count.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 1));  
    hm1.insert(Int_Pair(1, 4));  
    hm1.insert(Int_Pair(2, 1));  
  
    // Elements do not need to have unique keys in hash_multimap,  
    // so duplicates are allowed and counted  
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
The number of elements in hm1 with a sort key of 1 is: 2.  
The number of elements in hm1 with a sort key of 2 is: 2.  
The number of elements in hm1 with a sort key of 3 is: 0.  
```  
  
##  <a name="a-namehashmultimapcrbegina--hashmultimapcrbegin"></a><a name="hash_multimap__crbegin"></a>  hash_multimap::crbegin  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回常數迭代器，定址對象是反轉 hash_multimap 中的第一個元素。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 [hash_multimap](../standard-library/hash-multimap-class.md) 中的第一個元素，或未反轉 `hash_multimap` 中的最後一個元素。  
  
### <a name="remarks"></a>備註  
 `crbegin` 是與反轉 hash_multimap 搭配使用，就如同 [hash_multimap::begin](#hash_multimap__begin) 是與 `hash_multimap` 搭配使用一樣。  
  
 有 `crbegin` 的傳回值時，無法修改 `hash_multimap` 物件。  
  
 `crbegin` 可用來向後逐一查看 `hash_multimap`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_crbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="a-namehashmultimapcrenda--hashmultimapcrend"></a><a name="hash_multimap__crend"></a>  hash_multimap::crend  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回常數迭代器，定址對象是反轉 hash_multimap 中最後一個元素後面的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 [hash_multimap](../standard-library/hash-multimap-class.md) 中最後一個元素後面的位置 (未反轉 `hash_multimap` 中第一個元素前面的位置)。  
  
### <a name="remarks"></a>備註  
 `crend` 是與反轉 hash_multimap 搭配使用，就如同 [hash_multimap::end](#hash_multimap__end) 是與 hash_multimap 搭配使用一樣。  
  
 有 `crend` 的傳回值時，無法修改 `hash_multimap` 物件。  
  
 `crend` 可以用來測試反轉迭代器是否已到達其 hash_multimap 的結尾。  
  
 `crend` 所傳回的值不應該取值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_crend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crend( );  
   hm1_crIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="a-namehashmultimapdifferencetypea--hashmultimapdifferencetype"></a><a name="hash_multimap__difference_type"></a>  hash_multimap::difference_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種帶正負號的整數類型，可用來代表範圍 (介於迭代器所指的元素之間) 中 hash_multimap 的元素數目。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 `difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 ` first` 和 ` last` 之間範圍 *[ first,  last)* 內的項目數，包括 ` first` 所指的項目，以及上限到 ` last` 所指項目 (但不包含此項目) 的項目範圍。  
  
 請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別，但只有隨機存取容器 (例如 vector) 所提供的隨機存取迭代器，才支援迭代器之間的減法。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_difference_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
#include <algorithm>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(3, 20));  
  
    // The following will insert, because map keys  
    // do not need to be unique  
    hm1.insert(Int_Pair(2, 30));  
  
    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;  
    hm1_bIter = hm1.begin();  
    hm1_eIter = hm1.end();  
  
    // Count the number of elements in a hash_multimap  
    hash_multimap<int, int>::difference_type df_count = 0;  
    hm1_Iter = hm1.begin();  
    while (hm1_Iter != hm1_eIter)  
    {  
        df_count++;  
        hm1_Iter++;  
    }  
  
    cout << "The number of elements in the hash_multimap hm1 is: "  
         << df_count << "." << endl;  
  
    cout << "The keys of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> first;  
    cout << "." << endl;  
  
    cout << "The values of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
The number of elements in the hash_multimap hm1 is: 4.  
The keys of the mapped elements are: 1 2 2 3.  
The values of the mapped elements are: 10 20 30 20.  
```  
  
##  <a name="a-namehashmultimapemplacea--hashmultimapemplace"></a><a name="hash_multimap__emplace"></a>  hash_multimap::emplace  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 將就地建構的元素插入到 hash_multimap 中。  
  
```  
template <class ValTy>  
iterator emplace(ValTy&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` val`|用來移動建構要插入到 [hash_multimap](../standard-library/hash-multimap-class.md) 中之元素的值。|  
  
### <a name="return-value"></a>傳回值  
 `emplace` 成員函式會傳回迭代器，此迭代器指向新元素的插入位置。  
  
### <a name="remarks"></a>備註  
 元素的 [hash_multimap::value_type](#hash_multimap__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 從 Visual C++ .NET 2003 開始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_emplace.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(move(is1));  
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
  
##  <a name="a-namehashmultimapemplacehinta--hashmultimapemplacehint"></a><a name="hash_multimap__emplace_hint"></a>  hash_multimap::emplace_hint  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 將就地建構的元素 (含位置提示) 插入到 hash_multimap 中。  
  
```  
template <class ValTy>  
iterator emplace_hint(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|` val`|用來建構要插入到 [hash_multimap](../standard-library/hash-multimap-class.md) 中之元素的值，除非 `hash_multimap` 已經包含該元素 (或更廣泛地說，即索引鍵以同等方式排序的元素)。|  
|`_Where`|一個有關要從哪裡開始搜尋正確插入點的提示。|  
  
### <a name="return-value"></a>傳回值  
 [hash_multimap::emplace](#hash_multimap__emplace) 成員函式會傳回迭代器，此迭代器指向新元素在 `hash_multimap` 中的插入位置。  
  
### <a name="remarks"></a>備註  
 元素的 [hash_multimap::value_type](#hash_multimap__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 如果插入點緊接在 `_Where` 之後，便可以分攤的常數時間 (而不是對數時間) 進行插入。  
  
 從 Visual C++ .NET 2003 開始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_emplace_hint.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(hm1.begin(), move(is1));  
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
  
##  <a name="a-namehashmultimapemptya--hashmultimapempty"></a><a name="hash_multimap__empty"></a>  hash_multimap::empty  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 測試 hash_multimap 是否是空的。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 hash_multimap 是空的，即為 **true**；如果 hash_multimap 不是空的，則為 **false**。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_empty.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2;  
  
   typedef pair <int, int> Int_Pair;  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( hm1.empty( ) )  
      cout << "The hash_multimap hm1 is empty." << endl;  
   else  
      cout << "The hash_multimap hm1 is not empty." << endl;  
  
   if ( hm2.empty( ) )  
      cout << "The hash_multimap hm2 is empty." << endl;  
   else  
      cout << "The hash_multimap hm2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_multimap hm1 is not empty.  
The hash_multimap hm2 is empty.  
```  
  
##  <a name="a-namehashmultimapenda--hashmultimapend"></a><a name="hash_multimap__end"></a>  hash_multimap::end  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，定址對象是 hash_multimap 中最後一個元素後面的位置。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>傳回值  
 雙向迭代器，定址對象是 hash_multimap 中最後一個元素後面的位置。 如果 hash_multimap 是空的，則 hash_multimap::end == hash_multimap::begin。  
  
### <a name="remarks"></a>備註  
 **end** 是用來測試迭代器是否已到達其 hash_multimap 的結尾。  
  
 **end** 所傳回的值不應該被取值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_end.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="a-namehashmultimapequalrangea--hashmultimapequalrange"></a><a name="hash_multimap__equal_range"></a>  hash_multimap::equal_range  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回一組迭代器，分別指向 hash_multimap 中索引鍵大於指定索引鍵的第一個元素，以及指向 hash_multimap 中索引鍵等於或大於該索引鍵的第一個元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 hash_multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 一組迭代器，其中第一個是索引鍵的 [lower_bound](#hash_multimap__lower_bound)，第二個是索引鍵的 [upper_bound](#hash_multimap__upper_bound)。  
  
 若要存取成員函式所傳回之配對 `pr` 的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之配對 `pr` 的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_equal_range.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_multimap <int, int> IntMMap;  
   IntMMap hm1;  
   hash_multimap <int, int> :: const_iterator hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;  
   p1 = hm1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   hm1_RcIter = hm1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << hm1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = hm1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key less than 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2  
 in the hash_multimap hm1 is: 20.  
The upper bound of the element with a key of 2  
 in the hash_multimap hm1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The hash_multimap hm1 doesn't have an element with a key less than 4.  
```  
  
##  <a name="a-namehashmultimaperasea--hashmultimaperase"></a><a name="hash_multimap__erase"></a>  hash_multimap::erase  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 從指定的位置移除 hash_multimap 中的元素或元素範圍，或移除符合指定索引鍵的元素。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>參數  
 `_Where`  
 要從 hash_multimap 移除之元素的位置。  
  
 ` first`  
 從 hash_multimap 移除之第一個元素的位置。  
  
 ` last`  
 從 hash_multimap 移除之最後一個元素以外的最近位置。  
  
 ` key`  
 要從 hash_multimap 中移除之元素的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 若為前兩個成員函式，會移除任何元素之外指定第一個剩餘元素的雙向迭代器，或如果沒有這類元素存在，則為 hash_multimap 結尾的指標。  
  
 在第三個成員函式中，傳回已從 hash_multimap 移除的元素數。  
  
### <a name="remarks"></a>備註  
 成員函式永遠不會擲回例外狀況。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 hash_multimap::erase 成員函式。  
  
```  
// hash_multimap_erase.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2, hm3;  
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_multimap<int, int>::size_type n;  
    typedef pair<int, int> Int_Pair;  
  
    for (i = 1; i < 5; i++)  
    {  
        hm1.insert(Int_Pair (i, i) );  
        hm2.insert(Int_Pair (i, i*i) );  
        hm3.insert(Int_Pair (i, i-1) );  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hm1.begin();  
    hm1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, "  
         << "the hash_multimap hm1 is:";  
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hm2.begin();  
    Iter2 = --hm2.end();  
    hm2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_multimap hm2 is:";  
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    hm3.insert(Int_Pair (2, 5));  
    n = hm3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n"  
         << " the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hm3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hm3.begin();  
    hm3.erase(Iter1);  
  
    cout << "After another element with a key equal to that of the"  
         << endl;  
    cout  << " 2nd element is deleted, "  
          << "the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.  
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.  
After the element with a key of 2 is deleted,  
 the hash_multimap hm3 is: 0 2 3.  
The number of elements removed from hm3 is: 2.  
After another element with a key equal to that of the  
 2nd element is deleted, the hash_multimap hm3 is: 0 3.  
```  
  
##  <a name="a-namehashmultimapfinda--hashmultimapfind"></a><a name="hash_multimap__find"></a>  hash_multimap::find  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，定址對象是 hash_multimap 中索引鍵等於指定索引鍵的第一個元素位置。  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要以所搜尋之 hash_multimap 中元素的排序鍵比對的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 迭代器，定址對象是具有指定索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，則是 hash_multimap 中最後一個元素後面的位置。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回迭代器，定址對象是 hash_multimap 中，在根據小於可比較性關聯來引發排序的二元述詞下，其排序鍵**等於**引數索引鍵的元素。  
  
 如果將 **find** 的傳回值指派給 `const_iterator`，便無法修改 hash_multimap 物件。 如果將 **find** 的傳回值指派給 **iterator**，則可以修改 hash_multimap 物件。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_find.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(3, 20));  
    hm1.insert(Int_Pair(3, 30));  
  
    hm1_RcIter = hm1.find(2);  
    cout << "The element of hash_multimap hm1 with a key of 2 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    hm1_RcIter = hm1.find(3);  
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    // If no match is found for the key, end() is returned  
    hm1_RcIter = hm1.find(4);  
  
    if (hm1_RcIter == hm1.end())  
        cout << "The hash_multimap hm1 doesn't have an element "  
             << "with a key of 4." << endl;  
    else  
        cout << "The element of hash_multimap hm1 with a key of 4 is: "  
             << hm1_RcIter -> second << "." << endl;  
  
    // The element at a specific location in the hash_multimap can be  
    // found using a dereferenced iterator addressing the location  
    hm1_AcIter = hm1.end();  
    hm1_AcIter--;  
    hm1_RcIter = hm1.find(hm1_AcIter -> first);  
    cout << "The first element of hm1 with a key matching"  
         << endl << "that of the last element is: "  
         << hm1_RcIter -> second << "." << endl;  
  
    // Note that the first element with a key equal to  
    // the key of the last element is not the last element  
    if (hm1_RcIter == --hm1.end())  
        cout << "This is the last element of hash_multimap hm1."  
             << endl;  
    else  
        cout << "This is not the last element of hash_multimap hm1."  
             << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="a-namehashmultimapgetallocatora--hashmultimapgetallocator"></a><a name="hash_multimap__get_allocator"></a>  hash_multimap::get_allocator  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回一份用來建構 hash_multimap 的配置器物件複本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 hash_multimap 所使用的配置器。  
  
### <a name="remarks"></a>備註  
 hash_multimap 類別的配置器會指定此類別管理儲存體的方式。 「C++ 標準程式庫」容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int>::allocator_type hm1_Alloc;  
   hash_multimap <int, int>::allocator_type hm2_Alloc;  
   hash_multimap <int, double>::allocator_type hm3_Alloc;  
   hash_multimap <int, int>::allocator_type hm4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> hm2;  
   hash_multimap <int, double> hm3;  
  
   hm1_Alloc = hm1.get_allocator( );  
   hm2_Alloc = hm2.get_allocator( );  
   hm3_Alloc = hm3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm3.max_size( ) <<  "." << endl;  
  
   // The following line creates a hash_multimap hm4  
   // with the allocator of hash_multimap hm1.  
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );  
  
   hm4_Alloc = hm4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
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
  
##  <a name="a-namehashmultimaphashmultimapa--hashmultimaphashmultimap"></a><a name="hash_multimap__hash_multimap"></a>  hash_multimap::hash_multimap  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 建構一個空的 hash_multimap，或是某個其他 hash_multimap 之全部或部分複本的 hash_multimap。  
  
```  
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,  
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp);

 
hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp,  
    const Allocator& Al);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Al`|要用於此 hash_multimap 物件的儲存體配置器類別，預設為 `Allocator`。|  
|`Comp`|類型為 `const``Traits` 並用來排序 map 中元素的比較函式，預設為 `Traits`。|  
|`Right`|要從中複製所建構之集合的對應。|  
|`First`|要複製的元素範圍中第一個元素的位置。|  
|`Last`|超出要複製之元素範圍的第一個元素的位置。|  
|`IList`|要作為複製來源的 initializer_list。|  
  
### <a name="remarks"></a>備註  
 所有建構函式都會儲存一種配置器物件，此物件可管理 hash_multimap 的記憶體儲存，且之後藉由呼叫 [get_allocator](#hash_multimap__get_allocator) 即可傳回此物件。 在類別宣告中經常會省略 allocator 參數，而前處理巨集會用來取代替代配置器。  
  
 所有建構函式都會將其 hash_multimap 初始化。  
  
 所有建構函式都會儲存一個 `Traits` 類型的函式物件，此物件可用來在 hash_multimap 的索引鍵之間建立順序，且之後藉由呼叫 [key_comp](#hash_multimap__key_comp) 即可傳回此物件。  
  
 前三個建構函式會指定空的初始 hash_multimap，第二個建構函式會指定建立元素順序時所要使用的比較函式類型 ( `Comp`)，而第三個建構函式則會明確指定所要使用的配置器類型 ( `_Al`)。 關鍵字 `explicit` 會隱藏某些類型的自動類型轉換。  
  
 第四個建構函式會指定 hash_multimap `Right` 的複本。  
  
 接下來的三個建構函式會複製 map 的範圍 `First, Last)`，其中會以越來越明確的方式指定類別 **Traits** 的比較函式及配置器的類型。  
  
 第八個建構函式會移動 hash_multimap `Right`。  
  
 最後三個建構函式會使用 initializer_list。  
  
##  <a name="a-namehashmultimapinserta--hashmultimapinsert"></a><a name="hash_multimap__insert"></a>  hash_multimap::insert  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 將某個項目或項目範圍插入 hash_multimap 中。  
  
```  
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,  
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

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
  
|||  
|-|-|  
|參數|描述|  
|`Val`|要插入 hash_multimap 中的項目值，除非其中已包含了該項目，或是更廣泛性地，其中已包含索引鍵經過對等排序的項目。|  
|`Where`|要開始搜尋正確插入點之位置的提示。|  
|`First`|要從對應複製之第一個項目的位置。|  
|`Last`|要從對應複製之最後一個項目後方的位置。|  
  
### <a name="return-value"></a>傳回值  
 前兩個 `insert` 成員函式會傳回迭代器，指向新項目插入的位置。  
  
 第三個成員函式會使用要插入之項目的 initializer_list。  
  
 第四個成員函式會將項目值的序列插入對應至每個項目的對應，而這些項目是由指定集之範圍 `[First, Last)` 中的迭代器指定。  
  
 最後兩個 `insert` 成員函式的行為與前兩個相同，不過它們是用來移動建構插入的值。  
  
### <a name="remarks"></a>備註  
 元素的 [value_type](#hash_multimap__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 針對 `insert`的版本，如果插入點後緊接著 `Where`的話，可能會在分攤的常數時間插入，而不是對數時間。  
  
##  <a name="a-namehashmultimapiteratora--hashmultimapiterator"></a><a name="hash_multimap__iterator"></a>  hash_multimap::iterator  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供可讀取或修改 hash_multimap 中任何元素的雙向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>備註  
 hash_multimap 所定義的 **iterator** 會指向 [value_type](#hash_multimap__value_type) 的物件，value_type 的類型為 `pair`\< **const Key, Type**>，其第一個成員是元素的索引鍵，而第二個成員是該元素所持有的已對應資料。  
  
 若要對指向 hash_multimap 中某個元素的 **iterator**`Iter` 進行取值，請使用 **->** 運算子。  
  
 若要存取該元素的索引鍵值，請使用 `Iter` -> **first**，這等同於 (\* `Iter`). **first**。 若要存取該元素的已對應資料值，請使用 `Iter` -> **second**，這等同於 (\* `Iter`). **first**。  
  
 類型 **iterator** 可用來修改元素的值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 **iterator** 的範例，請參閱 [begin](#hash_multimap__begin) 的範例。  
  
##  <a name="a-namehashmultimapkeycompa--hashmultimapkeycomp"></a><a name="hash_multimap__key_comp"></a>  hash_multimap::key_comp  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 擷取一份用來排序 hash_multimap 中索引鍵的比較物件複本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 hash_multimap 用來排序其元素的函式物件。  
  
### <a name="remarks"></a>備註  
 預存物件會定義成員函式  
  
 **bool operator(const Key&** ` left` **, const Key&** ` right` **);**  
  
 如果 ` left` 在前面且在排序次序中不等於 ` right`，此函式就會傳回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_key_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int> > > hm1;  
   hash_multimap <int, int, hash_compare<int, less<int> >   
      >::key_compare kc1 = hm1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
  
   hash_multimap <int, int, hash_compare<int, greater<int> > > hm2;  
   hash_multimap <int, int, hash_compare<int, greater<int> >   
      >::key_compare kc2 = hm2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
}  
```  
  
##  <a name="a-namehashmultimapkeycomparea--hashmultimapkeycompare"></a><a name="hash_multimap__key_compare"></a>  hash_multimap::key_compare  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種提供函式物件的類型，該函式物件可比較兩個排序鍵來判斷 hash_multimap 中兩個元素的相對順序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>備註  
 **key_compare** 與範本參數 `Traits` 同義。  
  
 如需有關 `Traits` 的詳細資訊，請參閱 [hash_multimap 類別](../standard-library/hash-multimap-class.md)主題。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#hash_multimap__key_comp) 的範例。  
  
##  <a name="a-namehashmultimapkeytypea--hashmultimapkeytype"></a><a name="hash_multimap__key_type"></a>  hash_multimap::key_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，描述構成 hash_multimap 每個元素的排序鍵物件。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 `key_type` 與範本參數 `Key` 同義。  
  
 如需有關 `Key` 的詳細資訊，請參閱 [hash_multimap 類別](../standard-library/hash-multimap-class.md)主題的＜備註＞一節。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_compare` 的範例，請參閱 [value_type](#hash_multimap__value_type) 的範例。  
  
##  <a name="a-namehashmultimaplowerbounda--hashmultimaplowerbound"></a><a name="hash_multimap__lower_bound"></a>  hash_multimap::lower_bound  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，指向 hash_multimap 中索引鍵等於或大於指定索引鍵的第一個元素。  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 hash_multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 [iterator](#hash_multimap__iterator) 或 [const_iterator](#hash_multimap__const_iterator)，定址對象是 hash_multimap 中索引鍵等於或大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_multimap 中最後一個元素後面的位置。  
  
 如果將 `lower_bound` 的傳回值指派給 `const_iterator`，便無法修改 hash_multimap 物件。 如果將 `lower_bound` 的傳回值指派給 **iterator**，則可以修改 hash_multimap 物件。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter,   
      hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.lower_bound( 2 );  
   cout << "The element of hash_multimap hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.lower_bound( 3 );  
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key matching"  
        << endl << " that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // Note that the first element with a key equal to  
   // the key of the last element is not the last element  
   if ( hm1_RcIter == --hm1.end( ) )  
      cout << "This is the last element of hash_multimap hm1."  
           << endl;  
   else  
      cout << "This is not the last element of hash_multimap hm1."  
           << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
 that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="a-namehashmultimapmappedtypea--hashmultimapmappedtype"></a><a name="hash_multimap__mapped_type"></a>  hash_multimap::mapped_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，代表儲存在 hash_multimap 中的資料類型。  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>備註  
 `mapped_type` 與範本參數 `Type` 同義。  
  
 如需有關 `Type` 的詳細資訊，請參閱 [hash_multimap 類別](../standard-library/hash-multimap-class.md)主題。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#hash_multimap__value_type) 的範例。  
  
##  <a name="a-namehashmultimapmaxsizea--hashmultimapmaxsize"></a><a name="hash_multimap__max_size"></a>  hash_multimap::max_size  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回 hash_multimap 的最大長度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 hash_multimap 的最大可能長度。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_max_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: size_type i;  
  
   i = hm1.max_size( );  
   cout << "The maximum possible length "  
        << "of the hash_multimap is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namehashmultimapoperatoreqa--hashmultimapoperator"></a><a name="hash_multimap__operator_eq"></a>  hash_multimap::operator=  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 將 hash_multimap 的元素以另一個 hash_multimap 的複本取代。  
  
```  
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|` right`|要複製到 `hash_multimap` 中的 [hash_multimap](../standard-library/hash-multimap-class.md)。|  
  
### <a name="remarks"></a>備註  
 清除 `hash_multimap` 中的任何現有項目之後，`operator=` 會將 ` right` 的內容複製或移到 `hash_multimap` 中。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_operator_as.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> v1, v2, v3;  
   hash_multimap<int, int>::iterator iter;  
  
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
  
##  <a name="a-namehashmultimappointera--hashmultimappointer"></a><a name="hash_multimap__pointer"></a>  hash_multimap::pointer  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供 hash_multimap 中元素的指標。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 **pointer** 可用來修改元素的值。  
  
 在大多數情況下，應該使用 [iterator](#hash_multimap__iterator) 來存取 hash_multimap 物件中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
##  <a name="a-namehashmultimaprbegina--hashmultimaprbegin"></a><a name="hash_multimap__rbegin"></a>  hash_multimap::rbegin  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，定址對象是反轉 hash_multimap 中的第一個元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 hash_multimap 中的第一個元素，或未反轉 hash_multimap 中的最後一個元素。  
  
### <a name="remarks"></a>備註  
 `rbegin` 是與反轉 hash_multimap 搭配使用，就如同 [begin](#hash_multimap__begin) 是與 hash_multimap 搭配使用一樣。  
  
 如果將 `rbegin` 的傳回值指派給 `const_reverse_iterator`，便無法修改 hash_multimap 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改 hash_multimap 物件。  
  
 `rbegin` 可用來向後逐一查看 hash_multimap。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_rbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = hm1.rbegin( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "After the erasure, the first element"  
        << "\n in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the first element  
 in the reversed hash_multimap is 2.  
```  
  
##  <a name="a-namehashmultimapreferencea--hashmultimapreference"></a><a name="hash_multimap__reference"></a>  hash_multimap::reference  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供對儲存在 hash_multimap 中元素的參考。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_reference.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of first element in the hash_multimap is "  
        << Ref2 << "." << endl;  
  
   //The non-const_reference can be used to modify the   
   //data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="a-namehashmultimaprenda--hashmultimaprend"></a><a name="hash_multimap__rend"></a>  hash_multimap::rend  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，定址對象是反轉 hash_multimap 中最後一個元素後面的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 hash_multimap 中最後一個元素後面的位置 (未反轉 hash_multimap 中第一個元素前面的位置)。  
  
### <a name="remarks"></a>備註  
 `rend` 是與反轉 hash_multimap 搭配使用，就如同 [end](#hash_multimap__end) 是與 hash_multimap 搭配使用一樣。  
  
 如果將 `rend` 的傳回值指派給 [const_reverse_iterator](#hash_multimap__const_reverse_iterator)，便無法修改 hash_multimap 物件。 如果將 `rend` 的傳回值指派給 [reverse_iterator](#hash_multimap__reverse_iterator)，則可以修改 hash_multimap 物件。  
  
 `rend` 可以用來測試反轉迭代器是否已到達其 hash_multimap 的結尾。  
  
 `rend` 所傳回的值不應該取值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_rend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = --hm1.rend( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 1.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the last element in the reversed hash_multimap is 2.  
```  
  
##  <a name="a-namehashmultimapreverseiteratora--hashmultimapreverseiterator"></a><a name="hash_multimap__reverse_iterator"></a>  hash_multimap::reverse_iterator  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，提供可讀取或修改反轉 hash_multimap 中元素的雙向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `reverse_iterator` 是用來反向逐一查看 hash_multimap。  
  
 hash_multimap 所定義的 `reverse_iterator` 會指向 [value_type](#hash_multimap__value_type) 的物件，value_type 的類型為 `pair`\< **const Key, Type**>。 透過該配對的第一個成員，即可取得此索引鍵的值，而透過該配對的第二個成員，則可取得所對應元素的值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#hash_multimap__rbegin) 的範例。  
  
##  <a name="a-namehashmultimapsizea--hashmultimapsize"></a><a name="hash_multimap__size"></a>  hash_multimap::size  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回 hash_multimap 中的項目數。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 hash_multimap 的目前長度。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 hash_multimap::size 成員函式。  
  
```  
// hash_multimap_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    i = hm1.size();  
    cout << "The hash_multimap length is " << i << "." << endl;  
  
    hm1.insert(Int_Pair(2, 4));  
    i = hm1.size();  
    cout << "The hash_multimap length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_multimap length is 1.  
The hash_multimap length is now 2.  
```  
  
##  <a name="a-namehashmultimapsizetypea--hashmultimapsizetype"></a><a name="hash_multimap__size_type"></a>  hash_multimap::size_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種不帶正負號的整數類型，可計算 hash_multimap 中的元素數目。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#hash_multimap__size) 的範例  
  
##  <a name="a-namehashmultimapswapa--hashmultimapswap"></a><a name="hash_multimap__swap"></a>  hash_multimap::swap  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 交換兩個 hash_multimap 的元素。  
  
```  
void swap(hash_multimap& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供要交換之元素的 hash_multimap，或要與該 hash_multimap 交換元素的 hash_multimap。  
  
### <a name="remarks"></a>備註  
 任何參考、指標或迭代器只要指定的元素是在交換元素的兩個 hash_multimap 中，成員函式就不會使其失效。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_swap.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2, hm3;  
   hash_multimap <int, int>::iterator hm1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm2.insert ( Int_Pair ( 10, 100 ) );  
   hm2.insert ( Int_Pair ( 20, 200 ) );  
   hm3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hm1.swap( hm2 );  
  
   cout << "After swapping with hm2, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hm1, hm3 );  
  
   cout << "After swapping with hm3, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_multimap hm1 is: 10 20 30.  
After swapping with hm2, hash_multimap hm1 is: 100 200.  
After swapping with hm3, hash_multimap hm1 is: 300.  
```  
  
##  <a name="a-namehashmultimapupperbounda--hashmultimapupperbound"></a><a name="hash_multimap__upper_bound"></a>  hash_multimap::upper_bound  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 傳回迭代器，指向 hash_multimap 中索引鍵大於指定索引鍵的第一個元素。  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 hash_multimap 中元素的排序鍵比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 [iterator](#hash_multimap__iterator) 或 [const_iterator](#hash_multimap__const_iterator)，定址對象是 hash_multimap 中索引鍵大於引數索引鍵的元素位置，或如果找不到與該索引鍵相符的項目，定址對象就會是 hash_multimap 中最後一個元素後面的位置。  
  
 如果將 `upper_bound` 的傳回值指派給 `const_iterator`，便無法修改 hash_multimap 物件。 如果將 `upper_bound` 的傳回值指派給 **iterator**，則可以修改 hash_multimap 物件。  
  
### <a name="remarks"></a>備註  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm1.insert ( Int_Pair ( 3, 40 ) );  
  
   hm1_RcIter = hm1.upper_bound( 1 );  
   cout << "The 1st element of hash_multimap hm1 with "  
        << "a key greater than 1 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.upper_bound( 2 );  
   cout << "The first element of hash_multimap hm1\n with a key "  
        << " greater than 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.begin( );  
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key greater than"  
        << endl << " that of the initial element of hm1 is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.  
The first element of hash_multimap hm1  
 with a key  greater than 2 is: 30.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key greater than  
 that of the initial element of hm1 is: 20.  
```  
  
##  <a name="a-namehashmultimapvaluecompa--hashmultimapvaluecomp"></a><a name="hash_multimap__value_comp"></a>  hash_multimap::value_comp  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 成員函式會傳回函式物件，此物件可藉由比較 hash_multimap 中元素的索引鍵值來判斷這些元素的順序。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 hash_multimap 用來排序其元素的比較函式物件。  
  
### <a name="remarks"></a>備註  
 就 hash_multimap *m* 而言，如果兩個元素 *e*1( *k*1 *, d*1) 和 *e*2( *k*2 *, d*2) 是 [value_type](#hash_multimap__value_type) 類型的物件，其中 *k*1 和 *k*2 是其 [key_type](#hash_multimap__key_type) 類型的索引鍵，而 `d`1 和 `d`2 是其 [mapped_type](#hash_multimap__mapped_type) 類型的資料，則 *m.*`value_comp`( )( *e*1 *, e*2) 會等於 *m.*`key_comp`( ) ( *k*1 *, k*2)。 預存物件會定義成員函式  
  
 **bool operator**( **value_type&**` left`, **value_type&** ` right`);  
  
 如果 ` left` 的索引鍵值在前面且在排序次序中不等於 ` right` 的索引鍵值，此函式就會傳回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_value_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int> > > hm1;  
   hash_multimap <int, int, hash_compare<int, less<int> >   
      >::value_compare vc1 = hm1.value_comp( );  
   hash_multimap <int,int>::iterator Iter1, Iter2;  
  
   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );  
  
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
  
##  <a name="a-namehashmultimapvaluetypea--hashmultimapvaluetype"></a><a name="hash_multimap__value_type"></a>  hash_multimap::value_type  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 一種類型，代表儲存在 hash_multimap 中的物件類型。  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="remarks"></a>備註  
 `value_type` 會宣告為 `pair` *\<***const**[key_type](#hash_multimap__key_type), [mapped_type](#hash_multimap__mapped_type)> 而不是 `pair` *<*`key_type`*,* `mapped_type`*>*，因為無法使用非常數迭代器或參考來變更關聯容器的索引鍵。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// hash_multimap_value_type.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: key_type key1;  
   hash_multimap <int, int> :: mapped_type mapped1;  
   hash_multimap <int, int> :: value_type value1;  
   hash_multimap <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare another way to insert objects into a hash_multimap  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
  
   // Initializing key1 and mapped1  
   key1 = ( hm1.begin( ) -> first );  
   mapped1 = ( hm1.begin( ) -> second );  
  
   cout << "The key of first element in the hash_multimap is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the hash_multimap is "  
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
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The keys of the mapped elements are: 1 2.  
The values of the mapped elements are: 10 20.  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


