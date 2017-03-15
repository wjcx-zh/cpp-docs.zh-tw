---
title: "set 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::set
- set
- set/std::set
- std.set
dev_langs:
- C++
helpviewer_keywords:
- set class
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
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
ms.openlocfilehash: b779d47cdcf8d383b415b0412dcc77d8cdc78d7b
ms.lasthandoff: 02/24/2017

---
# <a name="set-class"></a>set 類別
C++ 標準程式庫容器類別 set 用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，並用來做為索引鍵值，據以自動排序資料。 集合中項目的索引鍵值不能直接變更。 相反地，必須刪除舊值，並插入具有新值的項目。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Key,   
    class Traits=less<Key>,   
    class Allocator=allocator<Key>>  
class set  
```  
  
#### <a name="parameters"></a>參數  
 `Key`  
 要存放在集合中的項目資料類型。  
  
 `Traits`  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在集合中的相對順序。 這是選擇性引數，而二元述詞 **less** *\<Key>* 為預設值。  
  
 在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)。  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關集合之記憶體配置和解除配置的詳細資訊。 這是選用引數，而預設值為 **allocator***\<Key>*。  
  
## <a name="remarks"></a>備註  
 C++ 標準程式庫 set 是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。 此外，它是簡單關聯的容器，因為其項目值是其索引鍵值的。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。  
  
-   唯一，因為它的每個項目都必須具有唯一索引鍵。 因為集合也是簡單的關聯容器，所以其元素也是唯一的。  
  
 集合也描述成樣板類別，因為它提供的功能是泛型，因此與做為項目包含的特定資料類型是獨立的。 使用的資料類型是在類別樣板中指定為參數 (和比較函式與配置器一起指定)。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 關聯的容器已針對查閱、插入和移除作業最佳化。 明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。 插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，集合應該是首選的關聯容器。 集合的項目是唯一的，並當做自己的排序鍵。 例如，這種結構的模型是文字的已排序清單，其中文字只可以出現一次。 如果允許文字的多個項目，則集合是適當的容器結構。 如果值必須附加至唯一關鍵字清單，則對應是包含這個資料的適當結構。 如果索引鍵不是唯一的，則多重對應是首選容器。  
  
 set 會藉由呼叫 [key_compare](#set__key_compare) 類型的預存函式物件，來排序它所控制的序列。 這個預存物件是可藉由呼叫成員函式 [key_comp](#set__key_comp) 來存取的比較函式。 通常，項目必須是小於比較才能建立此順序，因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。 二元述詞 *f*( *x,y*) 是一個函式物件，其中含有兩個引數物件 *x* 和 *y*，以及傳回值 **true** 或 **false**。 如果二元述詞為非自反、非對稱且可轉移的，而且如果等價是可轉移的，其中兩個物件 *x* 和 *y* 在 *f*( *x,y*) 和 *f*( *y,x*) 為 false 時定義為相等，則施加於 set 上的順序是嚴格弱式順序。 如果更強的索引鍵相等條件取代等價條件，順序會變成總計 (也就是所有項目彼此相關的排序)，因此相符的索引鍵之間將難以辨別。  
  
 在 C++14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。 如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)。  
  
 set 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](#set__insert) 和 [set](#set__set) 擁有以較弱的輸入迭代器做為樣板參數的版本，其功能需求較雙向迭代器類別所保證的還要基本。 不同的迭代器概念因其功能的修改而形成關聯的系列。 每個迭代器概念有自己的一組需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。 可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。 這是一組基本功能，不過，已足以在類別成員函式的內容中有意義地溝通迭代器範圍 [ `First`, `Last`)。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[set](#set__set)|建構一個空的集合，或者建構其他集合的全部或部分複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#set__allocator_type)|類型，表示 set 物件的 `allocator` 類別。|  
|[const_iterator](#set__const_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取集合中的 `const` 項目。|  
|[const_pointer](#set__const_pointer)|類型，提供集合中 `const` 項目之指標。|  
|[const_reference](#set__const_reference)|類型，提供儲存在集合中供讀取和執行 `const` 作業之 `const` 項目的參考。|  
|[const_reverse_iterator](#set__const_reverse_iterator)|提供雙向迭代器的類型，這個迭代器可以讀取集合中的任何 `const` 項目。|  
|[difference_type](#set__difference_type)|帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中集合的項目數。|  
|[iterator](#set__iterator)|類型，提供可以讀取或修改集合中之任何項目的雙向迭代器。|  
|[key_compare](#set__key_compare)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在集合中的相對順序。|  
|[key_type](#set__key_type)|此類型描述在做為排序鍵的產能上，做為集合的項目儲存的物件。|  
|[pointer](#set__pointer)|類型，提供集合中的項目之指標。|  
|[reference](#set__reference)|類型，提供儲存在集合中之項目的參考。|  
|[reverse_iterator](#set__reverse_iterator)|類型，提供可以讀取或修改反轉集合中之項目的雙向迭代器。|  
|[size_type](#set__size_type)|不帶正負號的整數類型，可以表示集合中的項目數。|  
|[value_compare](#set__value_compare)|類型，提供可比較兩個項目之函式物件，以判斷項目在集合中的相對順序。|  
|[value_type](#set__value_type)|此類型描述在做為值的產能上，做為集合的項目儲存的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[begin](#set__begin)|傳回迭代器，為集合中的第一個項目定址。|  
|[cbegin](#set__cbegin)|傳回常數迭代器，為集合中的第一個項目定址。|  
|[cend](#set__cend)|傳回常數迭代器，為集合中最後一個項目的下一個位置定址。|  
|[clear](#set__clear)|清除集合的所有項目。|  
|[count](#set__count)|傳回集合中索引鍵符合參數指定之索引鍵的項目數目。|  
|[crbegin](#set__rbegin)|傳回常數迭代器，為反轉集合中的第一個項目定址。|  
|[crend](#set__rend)|傳回常數迭代器，為反轉集合中最後一個項目的下一個位置定址。|  
|[emplace](#set__emplace)|將就地建構的項目插入集合中。|  
|[emplace_hint](#set__emplace_hint)|將就地建構的項目 (含位置提示) 插入集合中。|  
|[empty](#set__empty)|測試集合是否為空白。|  
|[end](#set__end)|傳回迭代器，為集合中最後一個項目的下一個位置定址。|  
|[equal_range](#set__equal_range)|傳回一組迭代器，分別指向集合中索引鍵大於特定索引鍵的第一個項目，以及指向集合中索引鍵等於或大於該索引鍵的第一個項目。|  
|[erase](#set__erase)|從指定的位置移除集合中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](#set__find)|傳回迭代器，定址集合中索引鍵等於指定索引鍵之項目的位置。|  
|[get_allocator](#set__get_allocator)|傳回用來建構集合的 `allocator` 物件複本。|  
|[insert](#set__insert)|將項目或某個項目範圍插入集合中。|  
|[key_comp](#set__key_comp)|擷取集合中用來排序索引鍵的比較物件之複本。|  
|[lower_bound](#set__lower_bound)|傳回迭代器，指向集合中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max_size](#set__max_size)|傳回集合的最大長度。|  
|[rbegin](#set__rbegin)|傳回迭代器，為反轉集合中的第一個項目定址。|  
|[rend](#set__rend)|傳回迭代器，為反轉集合中最後一個項目的下一個位置定址。|  
|[size](#set__size)|傳回集合中項目的數目。|  
|[swap](#set__swap)|交換兩個集合的項目。|  
|[upper_bound](#set__upper_bound)|傳回迭代器，指向集合中索引鍵大於特定索引鍵的第一個項目。|  
|[value_comp](#set__value_comp)|擷取集合中用於排序項目值的比較物件之複本。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator=](#set__operator_eq)|用另一個集合複本取代集合的項目。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<set>  
  
 **命名空間：** std  
  
##  <a name="a-namesetallocatortypea--setallocatortype"></a><a name="set__allocator_type"></a>  set::allocator_type  
 一種類型，代表 set 物件的配置器類別。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 **allocator_type** 與樣板參數 [Allocator](../standard-library/set-class.md) 同義。  
  
 傳回 multiset 用來排序其項目的函式物件，亦即樣板參數 `Allocator`。  
  
 如需 `Allocator` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題的＜備註＞一節。  
  
### <a name="example"></a>範例  
  如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#set__get_allocator) 的範例。  
  
##  <a name="a-namesetbegina--setbegin"></a><a name="set__begin"></a>  set::begin  
 傳回迭代器，為集合中的第一個項目定址。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>傳回值  
 一個雙向迭代器，定址對象是 set 中的第一個項目，或空 set 後面的位置。  
  
### <a name="remarks"></a>備註  
 如果將 **begin** 的傳回值指派給 `const_iterator`，則無法修改 set 物件中的項目。 如果將 **begin** 的傳回值指派給 **iterator**，則可修改 set 物件中的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_begin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::const_iterator s1_cIter;  
  
   s1.insert( 1 );  
   s1.insert( 2 );  
   s1.insert( 3 );  
  
   s1_Iter = s1.begin( );  
   cout << "The first element of s1 is " << *s1_Iter << endl;  
  
   s1_Iter = s1.begin( );  
   s1.erase( s1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // s1_cIter = s1.begin( );  
   // s1.erase( s1_cIter );  
  
   s1_cIter = s1.begin( );  
   cout << "The first element of s1 is now " << *s1_cIter << endl;  
}  
```  
  
```Output  
The first element of s1 is 1  
The first element of s1 is now 2  
```  
  
##  <a name="a-namesetcbegina--setcbegin"></a><a name="set__cbegin"></a>  set::cbegin  
 傳回 `const` 迭代器，為範圍中的第一個項目定址。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 `const` 雙向存取迭代器，指向範圍的第一個項目，或指向空白範圍結尾 (空白範圍 `cbegin() == cend()`) 之外的位置。  
  
### <a name="remarks"></a>備註  
 傳回值為 `cbegin` 時，無法修改範圍中的項目。  
  
 您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮將 `Container` 視為支援 `begin()` 和 `cbegin()`、任何種類的可修改 (非 `const`) 容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namesetcenda--setcend"></a><a name="set__cend"></a>  set::cend  
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
  
##  <a name="a-namesetcleara--setclear"></a><a name="set__clear"></a>  set::clear  
 清除集合的所有項目。  
  
```  
void clear();
```  
  
### <a name="example"></a>範例  
  
```cpp  
// set_clear.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
  
   s1.insert( 1 );  
   s1.insert( 2 );  
  
   cout << "The size of the set is initially " << s1.size( )  
        << "." << endl;  
  
   s1.clear( );  
   cout << "The size of the set after clearing is "   
        << s1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the set is initially 2.  
The size of the set after clearing is 0.  
```  
  
##  <a name="a-namesetconstiteratora--setconstiterator"></a><a name="set__const_iterator"></a>  set::const_iterator  
 一種類型，提供可讀取 set 中 **const** 項目的雙向迭代器。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_iterator` 無法用來修改元素的值。  
  
### <a name="example"></a>範例  
  如需使用 `const_iterator` 的範例，請參閱 [begin](#set__begin) 的範例。  
  
##  <a name="a-namesetconstpointera--setconstpointer"></a><a name="set__const_pointer"></a>  set::const_pointer  
 一種類型，提供 set 中 **const** 項目的指標。  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_pointer` 無法用來修改元素的值。  
  
 在大多數情況下，應該使用 [const_iterator](#set__const_iterator) 來存取 const set 物件中的項目。  
  
##  <a name="a-namesetconstreferencea--setconstreference"></a><a name="set__const_reference"></a>  set::const_reference  
 一種類型，提供儲存在 set 中用於讀取和執行 **const** 運算之 **const** 項目的參考。  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>範例  
  
```cpp  
// set_const_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *s1.begin( );  
  
   cout << "The first element in the set is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the set  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the set is 10.  
```  
  
##  <a name="a-namesetconstreverseiteratora--setconstreverseiterator"></a><a name="set__const_reverse_iterator"></a>  set::const_reverse_iterator  
 一種類型，提供可讀取 set 中任何 **const** 項目的雙向迭代器。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 `const_reverse_iterator` 類型無法修改項目的值，而是用來反向逐一查看 set。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `const_reverse_iterator` 的範例，請參閱 [rend](#set__rend) 的範例。  
  
##  <a name="a-namesetcounta--setcount"></a><a name="set__count"></a>  set::count  
 傳回集合中索引鍵符合參數指定之索引鍵的項目數目。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要從集合中比對之項目的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 1，表示集合包含其排序索引鍵符合參數索引鍵的項目。 0，表示集合不包含具有相符索引鍵的項目。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回下列範圍中的項目數：  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 set::count 成員函式。  
  
```  
// set_count.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    set<int> s1;  
    set<int>::size_type i;  
  
    s1.insert(1);  
    s1.insert(1);  
  
    // Keys must be unique in set, so duplicates are ignored  
    i = s1.count(1);  
    cout << "The number of elements in s1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = s1.count(2);  
    cout << "The number of elements in s1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in s1 with a sort key of 1 is: 1.  
The number of elements in s1 with a sort key of 2 is: 0.  
```  
  
##  <a name="a-namesetcrbegina--setcrbegin"></a><a name="set__crbegin"></a>  set::crbegin  
 傳回常數迭代器，為反轉集合中的第一個項目定址。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 set 中的第一個項目，或未反轉 set 中的最後一個項目。  
  
### <a name="remarks"></a>備註  
 `crbegin` 會與反轉 set 搭配使用，就如同 [begin](#set__begin) 與 set 搭配使用一樣。  
  
 有 `crbegin` 的傳回值時，就無法修改 set 物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_crbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_crIter = s1.crbegin( );  
   cout << "The first element in the reversed set is "  
        << *s1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed set is 30.  
```  
  
##  <a name="a-namesetcrenda--setcrend"></a><a name="set__crend"></a>  set::crend  
 傳回常數迭代器，為反轉集合中最後一個項目的下一個位置定址。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反轉雙向迭代器，定址對象是反轉 set 中最後一個項目的下一個位置 (此位置位於未反轉 set 中的第一個項目之前)。  
  
### <a name="remarks"></a>備註  
 `crend` 會與反轉 set 搭配使用，就如同 [end](#set__end) 與 set 搭配使用一樣。  
  
 有 `crend` 的傳回值時，就無法修改 set 物件。 `crend` 所傳回的值不應該取值。  
  
 `crend` 可用來測試反轉迭代器是否已到達其 set 的結尾。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_crend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   set <int> s1;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_crIter = s1.crend( );  
   s1_crIter--;  
   cout << "The last element in the reversed set is "  
        << *s1_crIter << "." << endl;  
}  
```  
  
##  <a name="a-namesetdifferencetypea--setdifferencetype"></a><a name="set__difference_type"></a>  set::difference_type  
 帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的項目) 中集合的項目數。  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 `difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 ` first` 和 ` last` 之間範圍 *[ first,  last)* 內的項目數，包括 ` first` 所指的項目，以及上限到 ` last` 所指項目 (但不包含此項目) 的項目範圍。  
  
 請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援的雙向迭代器類別，但只有隨機存取容器 (例如 vector) 所提供的隨機存取迭代器，才支援迭代器之間的減法。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   set <int> s1;  
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;  
  
   s1.insert( 20 );  
   s1.insert( 10 );  
   s1.insert( 20 );   // won't insert as set elements are unique  
  
   s1_bIter = s1.begin( );  
   s1_eIter = s1.end( );  
  
   set <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( s1_bIter, s1_eIter, 5 );  
   df_typ10 = count( s1_bIter, s1_eIter, 10 );  
   df_typ20 = count( s1_bIter, s1_eIter, 20 );  
  
   // the keys, and hence the elements of a set are unique,  
   // so there is at most one of a given value  
   cout << "The number '5' occurs " << df_typ5  
        << " times in set s1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in set s1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in set s1.\n";  
  
   // count the number of elements in a set  
   set <int>::difference_type  df_count = 0;  
   s1_Iter = s1.begin( );  
   while ( s1_Iter != s1_eIter)     
   {  
      df_count++;  
      s1_Iter++;  
   }  
  
   cout << "The number of elements in the set s1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in set s1.  
The number '10' occurs 1 times in set s1.  
The number '20' occurs 1 times in set s1.  
The number of elements in the set s1 is: 2.  
```  
  
##  <a name="a-namesetemplacea--setemplace"></a><a name="set__emplace"></a>  set::emplace  
 插入就地建構 (未執行任何複製或移動作業) 的項目。  
  
```  
template <class... Args>  
pair<iterator, bool>  
emplace(
    Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`args`|除非 set 已經包含值是以同等方式排序的項目，否則會轉送引數來建構要插入 set 的項目。|  
  
### <a name="return-value"></a>傳回值  
 如果已執行插入，即為 bool 元件會傳回 true 的 [pair](../standard-library/pair-structure.md)，如果 map 已經包含具有對等排序值的項目，則會傳回 false。 傳回值組的迭代器元件會傳回已插入新項目的位址 (如果 bool 元件為 true) 或項目已經存在的位址 (如果 bool 元件為 false)。  
  
### <a name="remarks"></a>備註  
 此函式不會使任何迭代器或參考失效。  
  
 在定位期間，如果擲回例外狀況，就不會修改容器的狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_emplace.cpp  
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
    set<string> s1;  
  
    auto ret = s1.emplace("ten");  
  
    if (!ret.second){  
        cout << "Emplace failed, element with value \"ten\" already exists."  
            << endl << "  The existing element is (" << *ret.first << ")"  
            << endl;  
        cout << "set not modified" << endl;  
    }  
    else{  
        cout << "set modified, now contains ";  
        print(s1);  
    }  
    cout << endl;  
  
    ret = s1.emplace("ten");  
  
    if (!ret.second){  
        cout << "Emplace failed, element with value \"ten\" already exists."  
            << endl << "  The existing element is (" << *ret.first << ")"  
            << endl;  
    }  
    else{  
        cout << "set modified, now contains ";  
        print(s1);  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namesetemplacehinta--setemplacehint"></a><a name="set__emplace_hint"></a>  set::emplace_hint  
 將就地建構 (未執行任何複製或移動作業) 的項目連同位置提示一起插入。  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`args`|除非 set 已經包含該項目，或者，更常見的說法是，除非它已經包含值是以同等方式排序的項目，否則會轉送引數來建構要插入 set 的項目。|  
|`where`|要開始搜尋正確的插入點的地方 (若該點緊接於 `where` 之前，則可能會在分攤常數時間插入，而不是對數時間)。|  
  
### <a name="return-value"></a>傳回值  
 新插入項目的迭代器。  
  
 如果插入因為項目已經存在而失敗，則會將迭代器傳回現有的項目。  
  
### <a name="remarks"></a>備註  
 此函式不會使任何迭代器或參考失效。  
  
 在定位期間，如果擲回例外狀況，就不會修改容器的狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_emplace.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: " << endl;  
  
    for (const auto& p : s) {  
        cout << "(" << p <<  ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    set<string> s1;  
  
    // Emplace some test data  
    s1.emplace("Anna");  
    s1.emplace("Bob");  
    s1.emplace("Carmine");  
  
    cout << "set starting data: ";  
    print(s1);  
    cout << endl;  
  
    // Emplace with hint  
    // s1.end() should be the "next" element after this emplacement  
    s1.emplace_hint(s1.end(), "Doug");  
  
    cout << "set modified, now contains ";  
    print(s1);  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namesetemptya--setempty"></a><a name="set__empty"></a>  set::empty  
 測試集合是否為空白。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 set 是空的，即為 **true**；如果 set 不是空的，則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_empty.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2;  
   s1.insert ( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The set s1 is empty." << endl;  
   else  
      cout << "The set s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The set s2 is empty." << endl;  
   else  
      cout << "The set s2 is not empty." << endl;  
}  
```  
  
```Output  
The set s1 is not empty.  
The set s2 is empty.  
```  
  
##  <a name="a-namesetenda--setend"></a><a name="set__end"></a>  set::end  
 傳回超出結尾 (past-the-end) 迭代器。  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>傳回值  
 超出結尾迭代器。 如果 set 是空的，則 `set::end() == set::begin()`。  
  
### <a name="remarks"></a>備註  
 **end** 可用來測試迭代器是否已超過其 set 的結尾。  
  
 不應該對 **end** 所傳回的值進行取值。  
  
 如需程式碼範例，請參閱 [set::find](#set__find)。  
  
##  <a name="a-namesetequalrangea--setequalrange"></a><a name="set__equal_range"></a>  set::equal_range  
 傳回一對迭代器，分別指向集合中索引鍵大於或大於特定索引鍵的第一個項目，以及指向集合中索引鍵等於該索引鍵的第一個項目。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 set 中項目的排序鍵進行比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 一對迭代器，其中第一個是索引鍵的 [lower_bound](#set__lower_bound)，第二個則是索引鍵的 [upper_bound](#set__upper_bound)。  
  
 若要存取成員函式所傳回之 `pr` 配對的第一個迭代器，請使用 `pr`. **first**，若要取下限迭代器的值，請使用 \*( `pr`. **first**)。 若要存取成員函式所傳回之 `pr` 配對的第二個迭代器，請使用 `pr`. **second**，若要取上限迭代器的值，請使用 \*( `pr`. **second**)。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_equal_range.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef set<int, less< int > > IntSet;  
   IntSet s1;  
   set <int, less< int > > :: const_iterator s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;  
   p1 = s1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the set s1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the set s1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   s1_RcIter = s1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *s1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = s1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of set s1 with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the set s1 is: 30.  
The lower bound of the element with a key of 20 in the set s1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The set s1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="a-nameseterasea--seterase"></a><a name="set__erase"></a>  set::erase  
 從指定的位置移除集合中的項目或項目範圍，或移除符合指定之索引鍵的項目。  
  
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
 緊接在要移除之最後一個項目後面的位置。  
  
 `Key`  
 要移除之項目的索引鍵值。  
  
### <a name="return-value"></a>傳回值  
 針對前兩個成員函式，會傳回雙向迭代器，其中指定移除任何項目後剩餘的第一個項目，或者，如果沒有這類項目，則傳回 set 結尾的項目。  
  
 針對第三個成員函式，傳回已從 set 移除的項目數。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
  
```cpp  
// set_erase.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
#include <iterator> // next() and prev() helper functions  
  
using namespace std;  
  
using myset = set<string>;  
  
void printset(const myset& s) {  
    for (const auto& iter : s) {  
        cout << " [" << iter << "]";  
    }  
    cout << endl << "size() == " << s.size() << endl << endl;  
}  
  
int main()  
{  
    myset s1;  
  
    // Fill in some data to test with, one at a time  
    s1.insert("Bob");  
    s1.insert("Robert");  
    s1.insert("Bert");  
    s1.insert("Rob");  
    s1.insert("Bobby");  
  
    cout << "Starting data of set s1 is:" << endl;  
    printset(s1);  
    // The 1st member function removes an element at a given position  
    s1.erase(next(s1.begin()));  
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;  
    printset(s1);  
  
    // Fill in some data to test with, one at a time, using an intializer list  
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };  
  
    cout << "Starting data of set s2 is:" << endl;  
    printset(s2);  
    // The 2nd member function removes elements  
    // in the range [First, Last)  
    s2.erase(next(s2.begin()), prev(s2.end()));  
    cout << "After the middle elements are deleted, the set s2 is:" << endl;  
    printset(s2);  
  
    myset s3;  
  
    // Fill in some data to test with, one at a time, using emplace  
    s3.emplace("C");  
    s3.emplace("C#");  
    s3.emplace("D");  
    s3.emplace("D#");  
    s3.emplace("E");  
    s3.emplace("E#");  
    s3.emplace("F");  
    s3.emplace("F#");  
    s3.emplace("G");  
    s3.emplace("G#");  
    s3.emplace("A");  
    s3.emplace("A#");  
    s3.emplace("B");  
  
    cout << "Starting data of set s3 is:" << endl;  
    printset(s3);  
    // The 3rd member function removes elements with a given Key  
    myset::size_type count = s3.erase("E#");  
    // The 3rd member function also returns the number of elements removed  
    cout << "The number of elements removed from s3 is: " << count << "." << endl;  
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;  
    printset(s3);  
}  
  
```  
  
##  <a name="a-namesetfinda--setfind"></a><a name="set__find"></a>  set::find  
 傳回迭代器，其表示 set 中索引鍵等於指定索引鍵的元素的位置。  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要以所搜尋之 set 中元素的排序鍵比對的索引鍵值。  
  
### <a name="return-value"></a>傳回值  
 一個迭代器，表示具有指定索引鍵的項目位置，或者，如果沒有找到索引鍵的相符項，則表示 set 中最後一個項目之後的位置 (`set::end()`)。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回迭代器，其表示 set 中排序鍵 (在二元述詞下根據較少的比較性關聯引發排序) 等於引數 `key` 的元素。  
  
 如果將 **find** 的傳回值指派給**const_iterator**，則無法修改 set 物件。 如果將 **find** 的傳回值指派給 **iterator**，則可修改 set 物件。  
  
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
    set<int> s1({ 40, 45 });  
    cout << "The starting set s1 is: " << endl;  
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
  
    cout << "The modified set s1 is: " << endl;  
    print_collection(s1);  
    cout << endl;  
    findit(s1, 45);  
    findit(s1, 6);  
}  
  
```  
  
##  <a name="a-namesetgetallocatora--setgetallocator"></a><a name="set__get_allocator"></a>  set::get_allocator  
 傳回用來建構 set 的配置器物件複本。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 set 用來管理記憶體的配置器，亦即樣板參數 `Allocator`。  
  
 如需 `Allocator` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題的＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 set 類別的配置器會指定類別如何管理儲存體。 C++ 標準程式庫容器類別隨附的預設配置器，就足以滿足大多數的程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_get_allocator.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int>::allocator_type s1_Alloc;  
   set <int>::allocator_type s2_Alloc;  
   set <double>::allocator_type s3_Alloc;  
   set <int>::allocator_type s4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   set <int> s1;  
   set <int, allocator<int> > s2;  
   set <double, allocator<double> > s3;  
  
   s1_Alloc = s1.get_allocator( );  
   s2_Alloc = s2.get_allocator( );  
   s3_Alloc = s3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << s2.max_size( ) << "." << endl;  
  
   cout << "\nThe number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << s3.max_size( ) <<  "." << endl;  
  
   // The following line creates a set s4  
   // with the allocator of multiset s1.  
   set <int> s4( less<int>( ), s1_Alloc );  
  
   s4_Alloc = s4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( s1_Alloc == s4_Alloc )  
   {  
      cout << "\nThe allocators are interchangeable."  
           << endl;  
   }  
   else  
   {  
      cout << "\nThe allocators are not interchangeable."  
           << endl;  
   }  
}  
```  
  
##  <a name="a-namesetinserta--setinsert"></a><a name="set__insert"></a>  set::insert  
 將項目或某個項目範圍插入集合中。  
  
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
|`Val`|除非其中包含了值已經過對等地排序的元素，否則為要插入 set 中的元素值。|  
|`Where`|要開始搜尋正確的插入點的地方 (若該點緊接於 `Where` 之前，則可能會在分攤常數時間插入，而不是對數時間)。|  
|`ValTy`|樣板參數，指定 set 可用於建構 [value_type](../standard-library/map-class.md#map__value_type) 項目的引數類型，並將 `Val` 當做引數完美轉送。|  
|`First`|要複製之第一個元素的位置。|  
|`Last`|要複製之最一個元素後方的位置。|  
|`InputIterator`|符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#map__value_type) 物件的類型。|  
|`IList`|要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>傳回值  
 單一項目成員函式 (1) 和 (2) 會傳回 [pair](../standard-library/pair-structure.md)，若已執行插入，其 `bool` 元件會是 true，若 set 已經包含對等排序值的項目，則為 false。 若 `bool` 元件為 True，傳回值組的迭代器元件會指向最新插入的元素；若 `bool` 元件為 False，則會指向現有元素。  
  
 具有提示的單一元素成員函式 (3) 及 (4) 會傳回指向位置的迭代器，該位置是新元素插入 set 中的位置，或者，若具有對等索引鍵的元素已存在，則指向現有元素。  
  
### <a name="remarks"></a>備註  
 此函式不會使任何迭代器、指標或參考無效。  
  
 在只插入一個元素的期間，若擲出例外狀況，則不會修改容器的狀態。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。  
  
 若要存取單一項目成員函式所傳回之 `pair``pr` 的迭代器元件，請使用 `pr.first`；若要對所傳回之 pair 內的迭代器進行取值，請使用 `*pr.first` 來提供項目。 若要存取 `bool` 元件，請使用 `pr.second`。 例如，請參閱本文中稍後的範例程式碼。  
  
 容器的 [value_type](../standard-library/map-class.md#map__value_type) 是屬於容器的 typedef，而針對 set，`set<V>::value_type` 是 `const V` 類型。  
  
 範圍成員函式 (5) 會將元素值序列插入 set，而 set 對應至範圍 `[First, Last)` 中迭代器指定的每個元素；因此不會插入 `Last`。 容器成員函式 `end()` 是指容器中最後一個項元素後方的位置；例如，陳述式 `s.insert(v.begin(), v.end());` 嘗試將 `v` 的所有元素插入 `s` 中。 只會插入具有範圍中唯一值的元素；若重複則會忽略。 若要觀察哪些元素會遭到拒絕，請使用單一元素版本的 `insert`。  
  
 初始設定式清單成員函式 (6) 會使用 [initializer_list](../standard-library/initializer-list.md)，將項目複製到 set。  
  
 若要了解如何插入就地建構 (也就是未執行任何複製或移動作業) 的項目，請參閱 [set::emplace](#set__emplace) 和 [set::emplace_hint](#set__emplace_hint)。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_insert.cpp  
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
    set<int> s1;  
    // call insert(const value_type&) version  
    s1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    s1.insert(20);  
  
    cout << "The original set values of s1 are:" << endl;  
    print(s1);  
  
    // intentionally attempt a duplicate, single element  
    auto ret = s1.insert(1);  
    if (!ret.second){  
        auto elem = *ret.first;  
        cout << "Insert failed, element with value 1 already exists."  
            << endl << "  The existing element is (" << elem << ")"  
            << endl;  
    }  
    else{  
        cout << "The modified set values of s1 are:" << endl;  
        print(s1);  
    }  
    cout << endl;  
  
    // single element, with hint  
    s1.insert(s1.end(), 30);  
    cout << "The modified set values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    set<int> s2;  
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
  
    cout << "The modified set values of s2 are:" << endl;  
    print(s2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    set<string>  s3;  
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
  
    set<int> s4;  
    // Insert the elements from an initializer_list  
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });  
    cout << "After initializer_list insertion, s4 contains:" << endl;  
    print(s4);  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namesetiteratora--setiterator"></a><a name="set__iterator"></a>  set::iterator  
 一種類型，提供可讀取 set 中任何項目的常數[雙向迭代器](../standard-library/bidirectional-iterator-tag-struct.md)。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 **iterator** 的範例，請參閱 [begin](#set__begin) 的範例。  
  
##  <a name="a-namesetkeycompa--setkeycomp"></a><a name="set__key_comp"></a>  set::key_comp  
 擷取集合中用來排序索引鍵的比較物件之複本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 set 用來排序其項目的函式物件，亦即樣板參數 `Traits`。  
  
 如需 `Traits` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題。  
  
### <a name="remarks"></a>備註  
 預存物件會定義成員函式：  
  
 **bool operator()**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 如果 `_xVal` 在前面且在排序次序中不等於 `_yVal`，此函式就會傳回 **true**。  
  
 請注意，[key_compare](#set__key_compare) 和 [value_compare](#set__value_compare) 都與樣板參數 **Traits** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_key_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   set <int, less<int> > s1;  
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;  
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
           << "where kc1 is the function object of s1."  
           << endl;  
   }  
  
   set <int, greater<int> > s2;  
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if(result2 == true)     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of s2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of s2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.  
```  
  
##  <a name="a-namesetkeycomparea--setkeycompare"></a><a name="set__key_compare"></a>  set::key_compare  
 類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在集合中的相對順序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>備註  
 `key_compare` 與樣板參數 `Traits` 同義。  
  
 如需 `Traits` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題。  
  
 請注意，`key_compare` 和 [value_compare](#set__value_compare) 都與樣板參數 **Traits** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_compare` 的範例，請參閱 [key_comp](#set__key_comp) 的範例。  
  
##  <a name="a-namesetkeytypea--setkeytype"></a><a name="set__key_type"></a>  set::key_type  
 一種類型，描述以set 的項目形式儲存且能夠做為排序鍵的物件。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 `key_type` 與樣板參數 `Key` 同義。  
  
 如需 `Key` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題的＜備註＞一節。  
  
 請注意，`key_type` 和 [value_type](#set__value_type) 都與樣板參數 **Key** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `key_type` 的範例，請參閱 [value_type](#set__value_type) 的範例。  
  
##  <a name="a-namesetlowerbounda--setlowerbound"></a><a name="set__lower_bound"></a>  set::lower_bound  
 傳回迭代器，指向集合中索引鍵等於或大於特定索引鍵的第一個項目。  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 set 中項目的排序鍵進行比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 iterator 或 `const_iterator`，定址對象是 set 中索引鍵等於或大於引數索引鍵的項目位置，或者，如果找不到與該索引鍵相符的項目，定址對象就是 set 中最後一個項目後面的位置。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_lower_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int> :: const_iterator s1_AcIter, s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_RcIter = s1.lower_bound( 20 );  
   cout << "The element of set s1 with a key of 20 is: "  
        << *s1_RcIter << "." << endl;  
  
   s1_RcIter = s1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( s1_RcIter == s1.end( ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of set s1 with a key of 40 is: "  
           << *s1_RcIter << "." << endl;  
  
   // The element at a specific location in the set can be found   
   // by using a dereferenced iterator that addresses the location  
   s1_AcIter = s1.end( );  
   s1_AcIter--;  
   s1_RcIter = s1.lower_bound( *s1_AcIter );  
   cout << "The element of s1 with a key matching "  
        << "that of the last element is: "  
        << *s1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of set s1 with a key of 20 is: 20.  
The set s1 doesn't have an element with a key of 40.  
The element of s1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="a-namesetmaxsizea--setmaxsize"></a><a name="set__max_size"></a>  set::max_size  
 傳回集合的最大長度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 set 的最大可能長度。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_max_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::size_type i;  
  
   i = s1.max_size( );     
   cout << "The maximum possible length "  
        << "of the set is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namesetoperatoreqa--setoperator"></a><a name="set__operator_eq"></a>  set::operator=  
 使用另一個 `set` 的項目來取代這個 `set` 的項目。  
  
```  
set& operator=(const set& right);

set& operator=(set&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` right`|`set` 會提供要指派給這個 `set` 的新項目。|  
  
### <a name="remarks"></a>備註  
 第一個 `operator=` 版本會使用 ` right` 的 [lvalue 參考](../cpp/lvalue-reference-declarator-amp.md)，將項目從 ` right` 複製到這個 `set`。  
  
 第二個版本會使用 right 的 [rvalue 參考](../cpp/rvalue-reference-declarator-amp-amp.md)。 它會將項目從 ` right` 移到這個 `set`。  
  
 這個 `set` 中的所有項目都會在運算子函式執行之前遭到捨棄。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_operator_as.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   set<int> v1, v2, v3;  
   set<int>::iterator iter;  
  
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
  
##  <a name="a-namesetpointera--setpointer"></a><a name="set__pointer"></a>  set::pointer  
 類型，提供集合中的項目之指標。  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 **pointer** 類型可用來修改項目的值。  
  
 在大部分情況下，應該使用 [iterator](#set__iterator) 來存取清單物件中的項目。  
  
##  <a name="a-namesetrbegina--setrbegin"></a><a name="set__rbegin"></a>  set::rbegin  
 傳回迭代器，為反轉集合中的第一個項目定址。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 set 中的第一個項目，或未反轉 set 中的最後一個項目。  
  
### <a name="remarks"></a>備註  
 `rbegin` 會與反轉 set 搭配使用，就如同 [begin](#set__begin) 與 set 搭配使用一樣。  
  
 如果將 `rbegin` 的傳回值指派給 `const_reverse_iterator`，則無法修改 set 物件。 如果將 `rbegin` 的傳回值指派給 `reverse_iterator`，則可修改 set 物件。  
  
 `rbegin` 可用來向後逐一查看 set。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_rbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::reverse_iterator s1_rIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_rIter = s1.rbegin( );  
   cout << "The first element in the reversed set is "  
        << *s1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a set in a forward order  
   cout << "The set is:";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a set in a reverse order  
   cout << "The reversed set is:";  
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )  
      cout << " " << *s1_rIter;  
   cout << endl;  
  
   // A set element can be erased by dereferencing to its key   
   s1_rIter = s1.rbegin( );  
   s1.erase ( *s1_rIter );  
  
   s1_rIter = s1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed set is "<< *s1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed set is 30.  
The set is: 10 20 30  
The reversed set is: 30 20 10  
After the erasure, the first element in the reversed set is 20.  
```  
  
##  <a name="a-namesetreferencea--setreference"></a><a name="set__reference"></a>  set::reference  
 類型，提供儲存在集合中之項目的參考。  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>範例  
  
```cpp  
// set_reference.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   const int &Ref1 = *s1.begin( );  
  
   cout << "The first element in the set is "  
        << Ref1 << "." << endl;  
}  
```  
  
```Output  
The first element in the set is 10.  
```  
  
##  <a name="a-namesetrenda--setrend"></a><a name="set__rend"></a>  set::rend  
 傳回迭代器，為反轉集合中最後一個項目的下一個位置定址。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>傳回值  
 反轉雙向迭代器，定址對象是反轉 set 中最後一個項目的下一個位置 (此位置位於未反轉 set 中的第一個項目之前)。  
  
### <a name="remarks"></a>備註  
 `rend` 會與反轉 set 搭配使用，就如同 [end](#set__end) 與 set 搭配使用一樣。  
  
 如果將 `rend` 的傳回值指派給 `const_reverse_iterator`，則無法修改 set 物件。 如果將 `rend` 的傳回值指派給 `reverse_iterator`，則可修改 set 物件。 `rend` 所傳回的值不應該取值。  
  
 `rend` 可用來測試反轉迭代器是否已到達其 set 的結尾。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_rend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::reverse_iterator s1_rIter;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_rIter = s1.rend( );  
   s1_rIter--;  
   cout << "The last element in the reversed set is "  
        << *s1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // throught a set in a forward order  
   cout << "The set is: ";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )  
      cout << *s1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // throught a set in a reverse order  
   cout << "The reversed set is: ";  
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )  
      cout << *s1_rIter << " ";  
   cout << "." << endl;  
  
   s1_rIter = s1.rend( );  
   s1_rIter--;  
   s1.erase ( *s1_rIter );  
  
   s1_rIter = s1.rend( );  
   --s1_rIter;  
   cout << "After the erasure, the last element in the "  
        << "reversed set is " << *s1_rIter << "." << endl;  
}  
```  
  
##  <a name="a-namesetreverseiteratora--setreverseiterator"></a><a name="set__reverse_iterator"></a>  set::reverse_iterator  
 類型，提供可以讀取或修改反轉集合中之項目的雙向迭代器。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 `reverse_iterator` 類型是用來反向逐一查看 set。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `reverse_iterator` 的範例，請參閱 [rbegin](#set__rbegin) 的範例。  
  
##  <a name="a-namesetseta--setset"></a><a name="set__set"></a>  set::set  
 建構一個空的集合，或者建構其他集合的全部或部分複本。  
  
```  
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,  
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,  
    const Compare& Comp);

set(
    initializer_list<Type> IList,  
    const Compare& Comp,   
    const Allocator& Al);

 
template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Al`|要用於此 set 物件的儲存體配置器類別，預設為 **Allocator**。|  
|`Comp`|`const Traits` 類型的比較函式，可用來排序 set 中的項目，預設為 `Compare`。|  
|`Rght`|要從中複製所建構之 set 的 set。|  
|`First`|要複製的元素範圍中第一個元素的位置。|  
|`Last`|超出要複製之元素範圍的第一個元素的位置。|  
|`IList`|從中複製項目的 initializer_list。|  
  
### <a name="remarks"></a>備註  
 所有建構函式都會儲存一種配置器物件，此物件可管理 set 的記憶體儲存，而且之後可藉由呼叫 [get_allocator](#set__get_allocator) 傳回此物件。 在類別宣告以及用來取代替代配置器的前置處理巨集中，經常會省略 allocator 參數。  
  
 所有建構函式都會將其 set 初始化。  
  
 所有建構函式都會儲存一個 **Traits** 類型的函式物件，此物件可用來在 set 的索引鍵之間建立順序，而且之後可藉由呼叫 [key_comp](#set__key_comp) 傳回此物件。  
  
 前三個建構函式會指定空的初始 set、第二個建構函式會指定建立項目順序時要使用的比較函式類型 ( `comp`)，而第三個建構函式則會明確指定要使用的配置器類型 ( `al`)。 關鍵字 **explicit** 會隱藏某些種類的自動類型轉換。  
  
 第四個建構函式會指定 set `right` 的複本。  
  
 接下來的三個建構函式會使用 initializer_list 來指定項目。  
  
 接下來的三個建構函式會複製 set 的範圍 [ `first`, `last`)，其會以越來越明確的方式指定類別 **Traits** 和 **Allocator** 的比較函式類型。  
  
 第八個建構函式會藉由移動 `right` 來指定 set 的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_set.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    // Create an empty set s0 of key type integer  
    set <int> s0;  
  
    // Create an empty set s1 with the key comparison  
    // function of less than, then insert 4 elements  
    set <int, less<int> > s1;  
    s1.insert(10);  
    s1.insert(20);  
    s1.insert(30);  
    s1.insert(40);  
  
    // Create an empty set s2 with the key comparison  
    // function of less than, then insert 2 elements  
    set <int, less<int> > s2;  
    s2.insert(10);  
    s2.insert(20);  
  
    // Create a set s3 with the   
    // allocator of set s1  
    set <int>::allocator_type s1_Alloc;  
    s1_Alloc = s1.get_allocator();  
    set <int> s3(less<int>(), s1_Alloc);  
    s3.insert(30);  
  
    // Create a copy, set s4, of set s1  
    set <int> s4(s1);  
  
    // Create a set s5 by copying the range s1[ first,  last)  
    set <int>::const_iterator s1_bcIter, s1_ecIter;  
    s1_bcIter = s1.begin();  
    s1_ecIter = s1.begin();  
    s1_ecIter++;  
    s1_ecIter++;  
    set <int> s5(s1_bcIter, s1_ecIter);  
  
    // Create a set s6 by copying the range s4[ first,  last)  
    // and with the allocator of set s2  
    set <int>::allocator_type s2_Alloc;  
    s2_Alloc = s2.get_allocator();  
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);  
  
    cout << "s1 =";  
    for (auto i : s1)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;  
  
    cout << "s3 =";  
    for (auto i : s3)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s4 =";  
    for (auto i : s4)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s5 =";  
    for (auto i : s5)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s6 =";  
    for (auto i : s6)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a set by moving s5  
    set<int> s7(move(s5));  
    cout << "s7 =";  
    for (auto i : s7)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a set with an initializer_list  
    cout << "s8 =";  
    set<int> s8{ { 1, 2, 3, 4 } };  
    for (auto i : s8)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s9 =";  
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };  
    for (auto i : s9)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s10 =";  
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };  
    for (auto i : s10)  
        cout << " " << i;  
    cout << endl;  
}  
  
```  
  
```Output  
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40  
```  
  
##  <a name="a-namesetsizea--setsize"></a><a name="set__size"></a>  set::size  
 傳回集合中項目的數目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 set 目前的長度。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int> :: size_type i;  
  
   s1.insert( 1 );  
   i = s1.size( );  
   cout << "The set length is " << i << "." << endl;  
  
   s1.insert( 2 );  
   i = s1.size( );  
   cout << "The set length is now " << i << "." << endl;  
}  
```  
  
```Output  
The set length is 1.  
The set length is now 2.  
```  
  
##  <a name="a-namesetsizetypea--setsizetype"></a><a name="set__size_type"></a>  set::size_type  
 不帶正負號的整數類型，可以表示集合中的項目數。  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#set__size) 的範例。  
  
##  <a name="a-namesetswapa--setswap"></a><a name="set__swap"></a>  set::swap  
 交換兩個集合的項目。  
  
```  
void swap(
    set<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供要與目標 set 交換之項目的引數 set。  
  
### <a name="remarks"></a>備註  
 任何參考、指標或迭代器只要指定的項目是在交換項目的兩個 set 中，成員函式就不會使其失效。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_swap.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   set <int>::iterator s1_Iter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
   s2.insert( 100 );  
   s2.insert( 200 );  
   s3.insert( 300 );  
  
   cout << "The original set s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   s1.swap( s2 );  
  
   cout << "After swapping with s2, list s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( s1, s3 );  
  
   cout << "After swapping with s3, list s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original set s1 is: 10 20 30.  
After swapping with s2, list s1 is: 100 200.  
After swapping with s3, list s1 is: 300.  
```  
  
##  <a name="a-namesetupperbounda--setupperbound"></a><a name="set__upper_bound"></a>  set::upper_bound  
 將迭代器傳回 set 中索引鍵大於指向索引鍵的第一個項目。  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>參數  
 ` key`  
 要與所搜尋之 set 中項目的排序鍵進行比較的引數索引鍵。  
  
### <a name="return-value"></a>傳回值  
 **iterator** 或 `const_iterator`，定址對象是 set 中索引鍵大於引數索引鍵的項目位置，或者，如果找不到與該索引鍵相符的項目，定址對象就是 set 中最後一個項目後面的位置。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_upper_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int> :: const_iterator s1_AcIter, s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_RcIter = s1.upper_bound( 20 );  
   cout << "The first element of set s1 with a key greater "  
        << "than 20 is: " << *s1_RcIter << "." << endl;  
  
   s1_RcIter = s1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( s1_RcIter == s1.end( ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key greater than 30." << endl;  
   else  
      cout << "The element of set s1 with a key > 40 is: "  
           << *s1_RcIter << "." << endl;  
  
   // The element at a specific location in the set can be found   
   // by using a dereferenced iterator addressing the location  
   s1_AcIter = s1.begin( );  
   s1_RcIter = s1.upper_bound( *s1_AcIter );  
   cout << "The first element of s1 with a key greater than"  
        << endl << "that of the initial element of s1 is: "  
        << *s1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of set s1 with a key greater than 20 is: 30.  
The set s1 doesn't have an element with a key greater than 30.  
The first element of s1 with a key greater than  
that of the initial element of s1 is: 20.  
```  
  
##  <a name="a-namesetvaluecompa--setvaluecomp"></a><a name="set__value_comp"></a>  set::value_comp  
 擷取集合中用於排序項目值的比較物件之複本。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 set 用來排序其項目的函式物件，亦即樣板參數 `Traits`。  
  
 如需 `Traits` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題。  
  
### <a name="remarks"></a>備註  
 預存物件會定義成員函式：  
  
 **bool operator**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 如果 `_xVal` 在前面且在排序次序中不等於 `_yVal`，此函式就會傳回 **true**。  
  
 請注意，[key_compare](#set__value_compare) 和 [value_compare](#set__key_compare) 都與樣板參數 **Traits** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_value_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   set <int, less<int> > s1;  
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )     
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of s1."  
           << endl;  
   }  
   else     
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of s1."  
           << endl;  
   }  
  
   set <int, greater<int> > s2;  
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )     
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of s2."  
           << endl;  
   }  
   else     
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of s2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.  
```  
  
##  <a name="a-namesetvaluecomparea--setvaluecompare"></a><a name="set__value_compare"></a>  set::value_compare  
 一種類型，提供可比較兩個項目值的函式物件，以判斷它們在 set 中的相對順序。  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>備註  
 `value_compare` 與樣板參數 `Traits` 同義。  
  
 如需 `Traits` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題。  
  
 請注意，[key_compare](#set__key_compare) 和 **value_compare** 都與樣板參數 **Traits** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `value_compare` 的範例，請參閱 [value_comp](#set__value_comp) 的範例。  
  
##  <a name="a-namesetvaluetypea--setvaluetype"></a><a name="set__value_type"></a>  set::value_type  
 一種類型，描述以set 的項目形式儲存且能夠做為值的物件。  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>備註  
 `value_type` 與樣板參數 `Key` 同義。  
  
 如需 `Key` 的詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)主題的＜備註＞一節。  
  
 請注意，[key_type](#set__key_type) 和 `value_type` 都與樣板參數 **Key** 同義。 針對 set 和 multiset 類別，會同時提供這兩種類型，其中兩者相同，而為了與 map 和 multimap 類別相容，其中兩者就會不同。  
  
### <a name="example"></a>範例  
  
```cpp  
// set_value_type.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int>::iterator s1_Iter;  
  
   set <int>::value_type svt_Int;   // Declare value_type  
   svt_Int = 10;            // Initialize value_type  
  
   set <int> :: key_type skt_Int;   // Declare key_type  
   skt_Int = 20;             // Initialize key_type  
  
   s1.insert( svt_Int );         // Insert value into s1  
   s1.insert( skt_Int );         // Insert key into s1  
  
   // A set accepts key_types or value_types as elements  
   cout << "The set has elements:";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)  
      cout << " " << *s1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The set has elements: 10 20.  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<set>](../standard-library/set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


