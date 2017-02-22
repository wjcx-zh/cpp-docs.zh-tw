---
title: "vector 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::vector"
  - "vector"
  - "std.vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector 類別"
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# 向量類別 1
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL 向量類別是序列容器的範本類別，以線性排列方式排列指定類型的項目，並允許快速隨機存取任何項目。 當隨機存取效能很重要時，這應該要當成慣用的序列容器。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type, class Allocator = allocator<Type>>  
class vector  
```  
  
#### <a name="parameters"></a>參數  
 *Type*  
 要儲存在向量中的項目資料類型  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關向量之記憶體配置和解除配置的詳細資料。 這個引數是選擇性的預設值是 **配置器***\< 類型>。*  
  
## <a name="remarks"></a>備註  
 向量可在序列結尾處插入和刪除常數時間。 在向量中間插入或刪除項目需要線性時間。 效能 [deque 類別](../standard-library/deque-class.md) 容器是可插入和刪除的開頭和結尾序列。  [List 類別](../standard-library/list-class.md) 容器是可在序列中的任何位置插入和刪除。  
  
 當成員函式必須將向量物件中包含的序列增加到超過其目前的儲存容量時，就會發生向量重新配置。 其他的插入和清除可能會改變序列中的各種儲存空間位址。 在這些情況下，指向改變之序列位置的迭代器或參考會變成無效。 如果沒有發生重新配置，只有插入/刪除點之前的迭代器和參考仍有效。  
  
  [向量 \< bool> 類別](../standard-library/vector-bool-class.md) 是完整特製化樣板類別向量的元素型別為 bool 的特製化所使用的基礎類型的配置器。  
  
  [向量 \< bool> 參考類別](../standard-library/vector-bool-class.md#vector_lt_bool_gt___reference_class) 是巢狀的類別，其物件可提供向量中的項目 （單一位元） 參考 \< bool> 物件。  
  
## <a name="members"></a>Members  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[向量](#vector__vector)|建構特定大小、具有特定值項目或具有特定 `allocator` 的向量，或將向量建構為其他一些向量的複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#vector__allocator_type)|代表向量物件之 `allocator` 類別的類型。|  
|[const_iterator](#vector__const_iterator)|提供可讀取向量中 `const` 項目之隨機存取迭代器的類型。|  
|[const_pointer](#vector__const_pointer)|提供向量中 `const` 項目之指標的類型。|  
|[const_reference](#vector__const_reference)|提供儲存在向量中供讀取和執行 `const` 作業之 `const` 項目參考的類型。|  
|[const_reverse_iterator](#vector__const_reverse_iterator)|提供可讀取向量中任何 `const` 項目之隨機存取迭代器的類型。|  
|[difference_type](#vector__difference_type)|提供向量中兩個項目位址之間差異的類型。|  
|[迭代器](#vector__iterator)|提供可讀取或修改向量中任何項目之隨機存取迭代器的類型。|  
|[指標](#vector__pointer)|提供向量中某個項目指標的類型。|  
|[參考](#vector__reference)|提供儲存在向量中之項目參考的類型。|  
|[reverse_iterator](#vector__reverse_iterator)|提供可讀取或修改反向向量中任何項目之隨機存取迭代器的類型。|  
|[size_type](#vector__size_type)|計算向量中項目數的類型。|  
|[value_type](#vector__value_type)|代表儲存在向量中之資料類型的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[指派](#vector__assign)|清除向量，並將指定的項目複製到空向量。|  
|[在](#vector__at)|傳回向量中指定位置的項目參考。|  
|[上一步]](#vector__back)|傳回向量的最後一個項目參考。|  
|[開始](#vector__begin)|傳回向量中第一個項目的隨機存取迭代器。|  
|[容量](#vector__capacity)|傳回向量可包含而不需要配置更多儲存空間的項目數。|  
|[cbegin](#vector__cbegin)|傳回向量中第一個項目的隨機存取常數迭代器。|  
|[cend](#vector__cend)|傳回隨機存取常數迭代器，指向向量結尾的後一個項目。|  
|[crbegin](#vector__crbegin)|將常數迭代器傳回至反向向量中的第一個項目。|  
|[crend](#vector__crend)|將常數迭代器傳回至反向向量的結尾。|  
|[清除](#vector__clear)|清除向量的項目。|  
|[資料](#vector__data)|傳回向量中第一個項目的指標。|  
|[emplace](#vector__emplace)|將就地建構的項目插入向量的指定位置。|  
|[emplace_back](#vector__emplace_back)|將就地建構的項目加入向量的結尾。|  
|[空白](#vector__empty)|測試向量容器是否空白。|  
|[結束](#vector__end)|傳回隨機存取迭代器，指向向量的結尾。|  
|[清除](#vector__erase)|從向量的指定位置移除一個項目或一定範圍的項目。|  
|[前端](#vector__front)|傳回向量中第一個項目的參考。|  
|[get_allocator](#vector__get_allocator)|將物件傳回至向量所使用的 `allocator` 類別。|  
|[插入](#vector__insert)|將就地建構的一個或多個項目插入向量的指定位置。|  
|[max_size](#vector__max_size)|傳回向量的最大長度。|  
|[pop_back](#vector__pop_back)|刪除向量結尾的元素。|  
|[push_back](#vector__push_back)|將項目加入向量的結尾。|  
|[rbegin](#vector__rbegin)|傳回反向向量中第一個項目的迭代器。|  
|[rend](#vector__rend)|將迭代器傳回至反向向量的結尾。|  
|[保留](#vector__reserve)|為向量物件保留最小儲存空間長度。|  
|[調整大小](#vector__resize)|指定向量的新大小。|  
|[shrink_to_fit](#vector__shrink_to_fit)|捨棄多餘的容量。|  
|[大小](#vector__size)|傳回向量中的項目數。|  
|[交換](#vector__swap)|交換兩個向量的項目。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 &#91; & #93。](#vector__operator_at)|傳回在指定位置上 vector 項目的參考。|  
|[運算子 =](#vector__operator_eq)|以另一個向量的複本取代向量的項目。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 向量>  
  
 **命名空間：** std  
  
##  <a name="a-namevectorallocatortypea-vectorallocatortype"></a><a name="vector__allocator_type"></a>  vector:: allocator_type  
 代表向量物件之配置器類別的類型。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 `allocator_type` 是範本參數的同義字 **配置器。**  
  
### <a name="example"></a>範例  
  請參閱範例 [get_allocator](#vector__get_allocator) 的範例會使用 `allocator_type`。  
  
##  <a name="a-namevectorassigna-vectorassign"></a><a name="vector__assign"></a>  vector:: assign  
 清除向量，並將指定的項目複製到空向量。  
  
```  
void assign(
    size_type Count,  
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);
```  
  
### <a name="parameters"></a>參數  
 `First`  
 項目範圍中要複製的第一個項目位置。  
  
 `Last`  
 項目範圍之外要複製的第一個項目位置。  
  
 `Count`  
 插入向量的項目複本數目。  
  
 `Val`  
 插入向量之項目的值。  
  
 `IList`  
 包含要插入之項目的 initializer_list。  
  
### <a name="remarks"></a>備註  
 清除向量中的任何現有項目之後，指派從原始向量將指定範圍的項目插入向量，或將指定值的新項目複本插入向量。  
  
### <a name="example"></a>範例  
  
```  
/ vector_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> v1, v2, v3;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(30);  
    v1.push_back(40);  
    v1.push_back(50);  
  
    cout << "v1 = ";  
    for (auto& v : v1){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v2.assign(v1.begin(), v1.end());  
    cout << "v2 = ";  
    for (auto& v : v2){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v3.assign(7, 4);  
    cout << "v3 = ";  
    for (auto& v : v3){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v3.assign({ 5, 6, 7 });  
    for (auto& v : v3){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namevectorata-vectorat"></a><a name="vector__at"></a>  vector:: at  
 傳回向量中指定位置的項目參考。  
  
```  
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 向量中要參考之項目的註標或位置編號。  
  
### <a name="return-value"></a>傳回值  
 引數中加上註標的項目參考。 如果 `_Off` 向量的大小大於 **在** 擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **在** 指派給 `const_reference`, ，無法修改向量物件。 如果傳回值 **在** 指派給 **參考**, ，可以修改向量物件。  
  
### <a name="example"></a>範例  
  
```  
// vector_at.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   const int &i = v1.at( 0 );  
   int &j = v1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namevectorbacka-vectorback"></a><a name="vector__back"></a>  vector:: back  
 傳回向量的最後一個項目參考。  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量的最後一個項目。 如果向量是空的，則傳回值不明。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **回** 指派給 `const_reference`, ，無法修改向量物件。 如果傳回值 **回** 指派給 **參考**, ，可以修改向量物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空向量中的項目，則會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// vector_back.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 11 );  
  
   int& i = v1.back( );  
   const int& ii = v1.front( );  
  
   cout << "The last integer of v1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of v1 is "<< ii << endl;  
}  
```  
  
##  <a name="a-namevectorbegina-vectorbegin"></a><a name="vector__begin"></a>  vector:: begin  
 傳回向量中第一個項目的隨機存取迭代器。  
  
```  
const_iterator begin() const;

 
iterator begin();
```  
  
### <a name="return-value"></a>傳回值  
 隨機存取迭代器定址中的第一個項目 `vector` 或下一個位置定址空白 `vector`。 您應該一律比較傳回的值與 [vector:: end](#vector__end) 以便確保它是否有效。  
  
### <a name="remarks"></a>備註  
 如果傳回值 `begin` 指派給 [vector:: const_iterator](#vector__const_iterator), 、 `vector` 無法修改物件。 如果傳回值 `begin` 指派給 [vector:: iterator](#vector__iterator), 、 `vector` 可以修改物件。  
  
### <a name="example"></a>範例  
  
```  
// vector_begin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> c1;  
    vector<int>::iterator c1_Iter;  
    vector<int>::const_iterator c1_cIter;  
  
    c1.push_back(1);  
    c1.push_back(2);  
  
    cout << "The vector c1 contains elements:";  
    c1_Iter = c1.begin();  
    for (; c1_Iter != c1.end(); c1_Iter++)  
    {  
        cout << " " << *c1_Iter;  
    }  
    cout << endl;  
  
    cout << "The vector c1 now contains elements:";  
    c1_Iter = c1.begin();  
 *c1_Iter = 20;  
    for (; c1_Iter != c1.end(); c1_Iter++)  
    {  
        cout << " " << *c1_Iter;  
    }  
    cout << endl;  
  
    // The following line would be an error because iterator is const  
    // *c1_cIter = 200;  
}  
```  
  
```Output  
The vector c1 contains elements: 1 2  
The vector c1 now contains elements: 20 2  
```  
  
##  <a name="a-namevectorcapacitya-vectorcapacity"></a><a name="vector__capacity"></a>  vector:: capacity  
 傳回向量可包含而不需要配置更多儲存空間的項目數。  
  
```  
size_type capacity() const;
```  
  
### <a name="return-value"></a>傳回值  
 目前配置給向量的儲存空間長度。  
  
### <a name="remarks"></a>備註  
 成員函式 [調整](#vector__resize) 會配置足夠的記憶體來容納它的更有效率。 使用成員函式 [保留](#vector__reserve) 指定配置的記憶體數量。  
  
### <a name="example"></a>範例  
  
```  
// vector_capacity.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 1 );  
   cout << "The length of storage allocated is "  
        << v1.capacity( ) << "." << endl;  
  
   v1.push_back( 2 );  
   cout << "The length of storage allocated is now "  
        << v1.capacity( ) << "." << endl;  
}  
```  
  
```Output  
The length of storage allocated is 1.  
The length of storage allocated is now 2.  
```  
  
##  <a name="a-namevectorcbegina-vectorcbegin"></a><a name="vector__cbegin"></a>  vector:: cbegin  
 傳回 `const` 迭代器，為範圍中的第一個項目定址。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 `const` 隨機存取迭代器，指向範圍的第一個項目，或指向空白範圍結尾 (空白範圍 `cbegin() == cend()`) 之外的位置。  
  
### <a name="remarks"></a>備註  
 傳回值為 `cbegin` 時，無法修改範圍中的項目。  
  
 您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 一般而言，它用於搭配 [自動](../cpp/auto-cpp.md) 類型推算關鍵字，如下列範例所示。 在範例中，請考慮 `Container` 的可修改 (非 `const`) 支援任何種類的容器 `begin()` 和 `cbegin()`。  
  
```cpp  
 
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namevectorcenda-vectorcend"></a><a name="vector__cend"></a>  vector:: cend  
 傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 指向範圍結尾之外的 `const` 隨機存取迭代器。  
  
### <a name="remarks"></a>備註  
 `cend` 用來測試迭代器是否已超過其範圍結尾。  
  
 您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 一般而言，它用於搭配 [自動](../cpp/auto-cpp.md) 類型推算關鍵字，如下列範例所示。 在範例中，請考慮 `Container` 的可修改 (非 `const`) 支援任何種類的容器 `end()` 和 `cend()`。  
  
```cpp  
 
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 `cend` 所傳回的值不應該取值。  
  
##  <a name="a-namevectorcleara-vectorclear"></a><a name="vector__clear"></a>  vector:: clear  
 清除向量的項目。  
  
```  
void clear();
```  
  
### <a name="example"></a>範例  
  
```  
// vector_clear.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "The size of v1 is " << v1.size( ) << endl;  
   v1.clear( );  
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;  
}  
```  
  
```Output  
The size of v1 is 3  
The size of v1 after clearing is 0  
```  
  
##  <a name="a-namevectorconstiteratora-vectorconstiterator"></a><a name="vector__const_iterator"></a>  vector:: const_iterator  
 類型，提供隨機存取迭代器可以讀取 **const** 向量中的項目。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_iterator` 無法用來修改元素的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [回](#vector__back) 的範例會使用 `const_iterator`。  
  
##  <a name="a-namevectorconstpointera-vectorconstpointer"></a><a name="vector__const_pointer"></a>  vector:: const_pointer  
 類型，提供一個指向 **const** 向量中的項目。  
  
```  
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_pointer` 無法用來修改元素的值。  
  
  [迭代器](#vector__iterator) 通常用來存取向量項目。  
  
##  <a name="a-namevectorconstreferencea-vectorconstreference"></a><a name="vector__const_reference"></a>  vector:: const_reference  
 提供的參考型別 **const** 供讀取和執行向量中儲存項目 **const** 作業。  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_reference` 無法用來修改元素的值。  
  
### <a name="example"></a>範例  
  
```  
// vector_const_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   const vector <int> v2 = v1;  
   const int &i = v2.front( );  
   const int &j = v2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as v2 is const  
   // v2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namevectorconstreverseiteratora-vectorconstreverseiterator"></a><a name="vector__const_reverse_iterator"></a>  vector:: const_reverse_iterator  
 類型，提供隨機存取迭代器可以讀取任何 **const** 向量的元素。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 型別 `const_reverse_iterator` 無法修改項目的值，且用來逐一查看反轉的向量。  
  
### <a name="example"></a>範例  
  請參閱 [rbegin](#vector__rbegin) 如需如何宣告和使用迭代器的範例。  
  
##  <a name="a-namevectorcrbegina-vectorcrbegin"></a><a name="vector__crbegin"></a>  vector:: crbegin  
 將常數迭代器傳回至反向向量中的第一個項目。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反向隨機存取迭代器定址反轉的第一個元件 [向量](../standard-library/vector-class.md) 或定址為未反轉的最後一個元素 `vector`。  
  
### <a name="remarks"></a>備註  
 有 `crbegin` 的傳回值時，無法修改 `vector` 物件。  
  
### <a name="example"></a>範例  
  
```  
// vector_crbegin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
   vector <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of vector is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed vector is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of vector is 1.  
The first element of the reversed vector is 2.  
```  
  
##  <a name="a-namevectorcrenda-vectorcrend"></a><a name="vector__crend"></a>  vector:: crend  
 傳回一個位置定址反向向量中的最後一個元素的 const 迭代器。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反向隨機存取迭代器定址反轉的最後一個元素的位置， [向量](../standard-library/vector-class.md) (必須在反轉之前的第一個元素的位置 `vector`)。  
  
### <a name="remarks"></a>備註  
 `crend` 使用與反轉 `vector` 就像 [vector:: cend](#vector__cend) 搭配 `vector`。  
  
 傳回的值是 `crend` （適當遞減）， `vector` 無法修改物件。  
  
 `crend` 可以用來測試反轉迭代器是否已到達其 `vector` 的結尾。  
  
 `crend` 所傳回的值不應該取值。  
  
### <a name="example"></a>範例  
  
```  
// vector_crend.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namevectordataa-vectordata"></a><a name="vector__data"></a>  vector:: data  
 傳回向量中第一個項目的指標。  
  
```  
const_pointer data() const;

 
pointer data();
```  
  
### <a name="return-value"></a>傳回值  
 第一個元素的指標 [向量](../standard-library/vector-class.md) 或下一個位置定址空白 `vector`。  
  
### <a name="example"></a>範例  
  
```  
// vector_data.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> c1;  
    vector<int>::pointer c1 ptr;  
    vector<int>::const_pointer c1_cPtr;  
  
    c1.push_back(1);  
    c1.push_back(2);  
  
    cout << "The vector c1 contains elements:";  
    c1_cPtr = c1.data();  
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)  
    {  
        cout << " " << *c1_cPtr;  
    }  
    cout << endl;  
  
    cout << "The vector c1 now contains elements:";  
    c1 ptr = c1.data();  
 *c1 ptr = 20;  
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)  
    {  
        cout << " " << *c1 ptr;  
    }  
    cout << endl;  
}  
```  
  
```Output  
The vector c1 contains elements: 1 2  
The vector c1 now contains elements: 20 2  
```  
  
##  <a name="a-namevectordifferencetypea-vectordifferencetype"></a><a name="vector__difference_type"></a>  vector:: difference_type  
 提供參考相同向量中項目之兩個迭代器間差異的類型。  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 A `difference_type` 也可以描述為兩個指標之間的項目數因為項目之指標包含它的位址。  
  
  [迭代器](#vector__iterator) 通常用來存取向量項目。  
  
### <a name="example"></a>範例  
  
```  
// vector_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <vector>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   vector <int> c1;  
   vector <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="a-namevectoremplacea-vectoremplace"></a><a name="vector__emplace"></a>  vector:: emplace  
 將就地建構的項目插入向量的指定位置。  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`_Where`|中的位置 [向量](../standard-library/vector-class.md) 插入的第一個元素的位置。|  
|` val`|插入 `vector` 的項目值。|  
  
### <a name="return-value"></a>傳回值  
 函式會傳回迭代器，指向新項目插入 `vector` 的位置。  
  
### <a name="remarks"></a>備註  
 任何插入作業都可能高度耗費資源，請參閱 [vector 類別](../standard-library/vector-class.md) 的討論 `vector` 效能。  
  
### <a name="example"></a>範例  
  
```  
// vector_emplace.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a vector of vectors by moving v1  
   vector < vector <int> > vv1;  
  
   vv1.emplace( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
vv1[0] = 10 20 30  
```  
  
##  <a name="a-namevectoremplacebacka-vectoremplaceback"></a><a name="vector__emplace_back"></a>  vector:: emplace_back  
 將就地建構的項目加入向量的結尾。  
  
```  
template <class... Types>  
void emplace_back(Types&&... _Args);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`_Args`|建構函式引數。 函式會根據所提供的引數推斷要叫用的建構函式多載。|  
  
### <a name="example"></a>範例  
  
```cpp  
  
#include <vector>  
struct obj  
{  
   obj(int, double) {}  
};  
  
int main()  
{  
   std::vector<obj> v;  
   v.emplace_back(1, 3.14); // obj in created in place in the vector  
}  
  
```  
  
##  <a name="a-namevectoremptya-vectorempty"></a><a name="vector__empty"></a>  vector:: empty  
 如果向量是空的，測試。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 **true** 如果向量是空的; **false** 如果向量不是空的。  
  
### <a name="example"></a>範例  
  
```  
// vector_empty.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
  
   if ( v1.empty( ) )  
      cout << "The vector is empty." << endl;  
   else  
      cout << "The vector is not empty." << endl;  
}  
```  
  
```Output  
The vector is not empty.  
```  
  
##  <a name="a-namevectorenda-vectorend"></a><a name="vector__end"></a>  vector:: end  
 傳回超出結尾 (past-the-end) 迭代器。  
  
```  
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量的超出結尾迭代器。 如果向量是空的，則為 `vector::end() == vector::begin()`。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **結束** 指派給類型的變數 `const_iterator`, ，無法修改向量物件。 如果傳回值 **結束** 指派給類型的變數 **迭代器**, ，可以修改向量物件。  
  
### <a name="example"></a>範例  
  
```  
// vector_end.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << endl;  
}  
```  
  
```Output  
1  
2  
```  
  
##  <a name="a-namevectorerasea-vectorerase"></a><a name="vector__erase"></a>  vector:: erase  
 從向量的指定位置移除一個項目或一定範圍的項目。  
  
```  
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`_Where`|要從向量中移除之項目的位置。|  
|` first`|從向量中移除之第一個項目的位置。|  
|` last`|從向量中移除的最後一個項目之後的位置。|  
  
### <a name="return-value"></a>傳回值  
 迭代器，指定任何移除的項目之後的第一個剩餘項目；如果沒有這個項目，則為向量結尾的指標。  
  
### <a name="example"></a>範例  
  
```  
// vector_erase.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
   v1.push_back( 40 );  
   v1.push_back( 50 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.erase( v1.begin( ) );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
}  
```  
  
```Output  
v1 = 10 20 30 40 50  
v1 = 20 30 40 50  
v1 = 20 50  
```  
  
##  <a name="a-namevectorfronta-vectorfront"></a><a name="vector__front"></a>  vector:: front  
 傳回向量中第一個項目的參考。  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量物件中第一個項目的參考。 如果向量是空的，則傳回不明。  
  
### <a name="remarks"></a>備註  
 如果 `front` 的傳回值已指派給 `const_reference`，則無法修改向量物件。 如果傳回值 `front` 指派給 **參考**, ，可以修改向量物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空向量中的項目，則會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// vector_front.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 11 );  
  
   int& i = v1.front( );  
   const int& ii = v1.front( );  
  
   cout << "The first integer of v1 is "<< i << endl;  
   // by incrementing i, we move the the front reference to the second element  
   i++;  
   cout << "Now, the first integer of v1 is "<< i << endl;  
}  
```  
  
##  <a name="a-namevectorgetallocatora-vectorgetallocator"></a><a name="vector__get_allocator"></a>  vector:: get_allocator  
 傳回用來建構向量的配置器物件複本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量所使用的配置器。  
  
### <a name="remarks"></a>備註  
 所指定的向量類別的配置器類別如何管理儲存體。 預設配置器所提供的STL 容器類別，已足夠大多數的程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。  
  
### <a name="example"></a>範例  
  
```  
// vector_get_allocator.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   vector<int> v1;  
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;  
  
   // v3 will use the same allocator class as v1  
   vector <int> v3( v1.get_allocator( ) );  
  
   vector<int>::allocator_type xvec = v3.get_allocator( );  
   // You can now call functions on the allocator class used by vec  
}  
```  
  
##  <a name="a-namevectorinserta-vectorinsert"></a><a name="vector__insert"></a>  vector:: insert  
 將一個項目、多個項目或一定範圍的項目插入向量的指定位置。  
  
```  
iterator insert(
    const_iterator _Where,  
    const Type& val);

iterator insert(
    const_iterator _Where,  
    Type&& val);

void insert(
    const_iterator _Where,  
    size_type count,  
    const Type& val);

template <class InputIterator>  
void insert(
    const_iterator _Where,  
    InputIterator first,  
    InputIterator last);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`_Where`|第一個項目插入向量中的位置。|  
|` val`|插入向量之項目的值。|  
|` count`|插入向量的項目數。|  
|` first`|要複製的元素範圍中第一個元素的位置。|  
|` last`|超出要複製之元素範圍的第一個元素的位置。|  
  
### <a name="return-value"></a>傳回值  
 前兩個 `insert` 函式會傳回迭代器，指向新項目插入向量的位置。  
  
### <a name="remarks"></a>備註  
 任何插入作業都可能高度耗費資源，請參閱 [vector 類別](../standard-library/vector-class.md) 的討論 `vector` 效能。  
  
### <a name="example"></a>範例  
  
```  
// vector_insert.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.insert( v1.begin( ) + 1, 40 );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
   v1.insert( v1.begin( ) + 2, 4, 50 );  
  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.insert( v1.begin( )+1, v1.begin( )+2, v1.begin( )+4 );  
   cout << "v1 =";  
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a vector of vectors by moving v1  
   vector < vector <int> > vv1;  
  
   vv1.insert( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      vector < vector <int> >::iterator Iter;  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
v1 = 10 40 20 30  
v1 = 10 40 50 50 50 50 20 30  
v1 = 10 50 50 40 50 50 50 50 20 30  
vv1[0] = 10 50 50 40 50 50 50 50 20 30  
```  
  
##  <a name="a-namevectoriteratora-vectoriterator"></a><a name="vector__iterator"></a>  vector:: iterator  
 提供可讀取或修改向量中任何項目之隨機存取迭代器的類型。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>備註  
 型別 **迭代器** 可以用來修改項目的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [開始](#vector__begin)。  
  
##  <a name="a-namevectormaxsizea-vectormaxsize"></a><a name="vector__max_size"></a>  vector:: max_size  
 傳回向量的最大長度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量的最大可能長度。  
  
### <a name="example"></a>範例  
  
```  
// vector_max_size.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::size_type i;  
  
   i = v1.max_size( );     
   cout << "The maximum possible length of the vector is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namevectoroperatorata-vectoroperator"></a><a name="vector__operator_at"></a>  vector:: operator]  
 傳回在指定位置上 vector 項目的參考。  
  
```  
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Pos`|vector 項目的位置。|  
  
### <a name="return-value"></a>傳回值  
 如果指定的位置大於或等於容器大小，則結果是未定義。  
  
### <a name="remarks"></a>備註  
 如果 `operator[]` 的傳回值已指派給 `const_reference`，則無法修改向量物件。 如果 `operator[]` 的傳回值已指派給參考，則可以修改向量物件。  
  
 使用 _SECURE_SCL 1 編譯時 (透過控制 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md))，如果您嘗試存取向量界限以外的項目，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   int& i = v1[1];  
   cout << "The second integer of v1 is " << i << endl;  
}  
```  
  
##  <a name="a-namevectoroperatoreqa-vectoroperator"></a><a name="vector__operator_eq"></a>  vector:: =  
 以另一個向量的複本取代向量的項目。  
  
```  
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` right`| [向量](../standard-library/vector-class.md) 複製到 `vector`。|  
  
### <a name="remarks"></a>備註  
 清除 `vector` 中的任何現有項目之後，`operator=` 會將 ` right` 的內容複製或移到 `vector` 中。  
  
### <a name="example"></a>範例  
  
```  
// vector_operator_as.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int> v1, v2, v3;  
   vector<int>::iterator iter;  
  
   v1.push_back(10);  
   v1.push_back(20);  
   v1.push_back(30);  
   v1.push_back(40);  
   v1.push_back(50);  
  
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
  
##  <a name="a-namevectorpointera-vectorpointer"></a><a name="vector__pointer"></a>  vector:: pointer  
 提供向量中某個項目指標的類型。  
  
```  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 型別 **指標** 可以用來修改項目的值。  
  
### <a name="example"></a>範例  
  
```  
// vector_pointer.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int> v;  
   v.push_back( 11 );  
   v.push_back( 22 );  
  
   vector<int>::pointer ptr = &v[0];  
   cout << *ptr << endl;  
   ptr++;  
   cout << *ptr << endl;  
 *ptr = 44;  
   cout << *ptr << endl;  
}  
```  
  
```Output  
11  
22  
44  
```  
  
##  <a name="a-namevectorpopbacka-vectorpopback"></a><a name="vector__pop_back"></a>  vector:: pop_back  
 刪除向量結尾的元素。  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>備註  
 如需程式碼範例，請參閱 [vector:: push_back （)](#vector__push_back)。  
  
##  <a name="a-namevectorpushbacka-vectorpushback"></a><a name="vector__push_back"></a>  vector:: push_back  
 將元素加入至向量結尾。  
  
```  
void push_back(const T& Val);

 
void push_back(T&& Val);
```  
  
### <a name="parameters"></a>參數  
 `Val`  
 要指派給加入到向量結尾之元素的值。  
  
### <a name="example"></a>範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
template <typename T> void print_elem(const T& t) {  
    cout << "(" << t << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << "  " << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(10 + i);  
    }  
  
    cout << "vector data: " << endl;  
    print_collection(v);  
  
    // pop_back() until it's empty, printing the last element as we go  
    while (v.begin() != v.end()) {   
        cout << "v.back(): "; print_elem(v.back()); cout << endl;  
        v.pop_back();  
    }  
}  
```  
  
##  <a name="a-namevectorrbegina-vectorrbegin"></a><a name="vector__rbegin"></a>  vector:: rbegin  
 傳回反向向量中第一個項目的迭代器。  
  
```  
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 反向隨機存取迭代器定址反向向量中的第一個項目，或為未反轉向量中的最後一個項目定址。  
  
### <a name="remarks"></a>備註  
 如果 `rbegin` 的傳回值已指派給 `const_reverse_iterator`，則無法修改向量物件。 如果傳回值 `rbegin` 指派給 `reverse_iterator`, ，可以修改向量物件。  
  
### <a name="example"></a>範例  
  
```  
// vector_rbegin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
   vector <int>::reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of vector is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.rbegin( );  
   cout << "The first element of the reversed vector is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of vector is 1.  
The first element of the reversed vector is 2.  
```  
  
##  <a name="a-namevectorreferencea-vectorreference"></a><a name="vector__reference"></a>  vector:: reference  
 提供儲存在向量中之項目參考的類型。  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>範例  
  請參閱 [在](#vector__at) 如需如何使用 **參考** 向量類別中。  
  
##  <a name="a-namevectorrenda-vectorrend"></a><a name="vector__rend"></a>  vector:: rend  
 傳回反向向量中的最後一個元素之後的位置的迭代器。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>傳回值  
 反向隨機存取迭代器位置定址反向向量 （有前面加上反轉向量中的第一個項目位置） 中的最後一個項目。  
  
### <a name="remarks"></a>備註  
 `rend` 用於反向向量一樣 [結束](#vector__end) 用於向量。  
  
 如果傳回值 `rend` 指派給 `const_reverse_iterator`, ，則無法修改向量物件。 如果傳回值 `rend` 指派給 `reverse_iterator`, ，則可以修改向量物件。  
  
 `rend` 可用來測試反轉迭代器是否已到達其向量的結尾。  
  
 `rend` 所傳回的值不應該取值。  
  
### <a name="example"></a>範例  
  
```  
// vector_rend.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namevectorreservea-vectorreserve"></a><a name="vector__reserve"></a>  vector:: reserve  
 為向量物件保留最小儲存空間長度，並在必要時配置空間。  
  
```  
void reserve(size_type count);
```  
  
### <a name="parameters"></a>參數  
 ` count`  
 配置給向量的最小儲存空間長度。  
  
### <a name="example"></a>範例  
  
```  
// vector_reserve.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   //vector <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.reserve( 20 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
}  
```  
  
```Output  
Current capacity of v1 = 1  
Current capacity of v1 = 20  
```  
  
##  <a name="a-namevectorresizea-vectorresize"></a><a name="vector__resize"></a>  vector:: resize  
 指定向量的新大小。  
  
```  
void resize(size_type Newsize);

void resize(size_type Newsize, Type Val);
```  
  
### <a name="parameters"></a>參數  
 `Newsize`  
 向量的新大小。  
  
 `Val`  
 如果新的大小大於原始大小，則已將新元素的初始化值加入至向量。 如果省略此值，則新的物件會使用其預設建構函式。  
  
### <a name="remarks"></a>備註  
 如果容器的大小小於所要求的大小 (`Newsize`)，則除非達到所要求的大小，否則會將元素加入至向量。 如果容器的大小大於所要求的大小，則除非容器達到大小 `Newsize`，否則會刪除最接近容器結尾的元素。 如果容器現在的大小與所要求的大小相同，則不會採取任何動作。  
  
 [大小](#vector__size) 會反映向量的目前大小。  
  
### <a name="example"></a>範例  
  
```cpp  
// vectorsizing.cpp  
// compile with: /EHsc /W4  
// Illustrates vector::reserve, vector::max_size,  
// vector::resize, vector::resize, and vector::capacity.  
//  
// Functions:  
//  
//    vector::max_size - Returns maximum number of elements vector could  
//                       hold.  
//  
//    vector::capacity - Returns number of elements for which memory has  
//                       been allocated.  
//  
//    vector::size - Returns number of elements in the vector.  
//  
//    vector::resize - Reallocates memory for vector, preserves its  
//                     contents if new size is larger than existing size.  
//  
//    vector::reserve - Allocates elements for vector to ensure a minimum  
//                      size, preserving its contents if the new size is  
//                      larger than existing size.  
//  
//    vector::push_back - Appends (inserts) an element to the end of a  
//                        vector, allocating memory for it if necessary.  
//  
//////////////////////////////////////////////////////////////////////  
  
// The debugger cannot handle symbols more than 255 characters long.  
// STL often creates symbols longer than that.  
// The warning can be disabled:  
//#pragma warning(disable:4786)  
  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
    cout << endl;  
}  
  
void printvstats(const vector<int>& v) {  
    cout << "   the vector's size is: " << v.size() << endl;  
    cout << "   the vector's capacity is: " << v.capacity() << endl;  
    cout << "   the vector's maximum size is: " << v.max_size() << endl;  
}  
  
int main()  
{  
    // declare a vector that begins with 0 elements.  
    vector<int> v;  
  
    // Show statistics about vector.  
    cout << endl << "After declaring an empty vector:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    // Add one element to the end of the vector.  
    v.push_back(-1);  
    cout << endl << "After adding an element:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    for (int i = 1; i < 10; ++i) {  
        v.push_back(i);  
    }  
    cout << endl << "After adding 10 elements:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(6);  
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(9, 999);  
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(12);  
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    // Ensure there's room for at least 1000 elements.  
    v.reserve(1000);  
    cout << endl << "After vector::reserve(1000):" << endl;  
    printvstats(v);  
  
    // Ensure there's room for at least 2000 elements.  
    v.resize(2000);  
    cout << endl << "After vector::resize(2000):" << endl;  
    printvstats(v);  
}  
```  
  
##  <a name="a-namevectorreverseiteratora-vectorreverseiterator"></a><a name="vector__reverse_iterator"></a>  vector:: reverse_iterator  
 提供可讀取或修改反向向量中任何項目之隨機存取迭代器的類型。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `reverse_iterator` 可用來反向逐一查看向量。  
  
### <a name="example"></a>範例  
  請參閱範例 [rbegin](#vector__rbegin)。  
  
##  <a name="a-namevectorshrinktofita-vectorshrinktofit"></a><a name="vector__shrink_to_fit"></a>  vector:: shrink_to_fit  
 捨棄多餘的容量。  
  
```  
void shrink_to_fit();
```  
  
### <a name="example"></a>範例  
  
```  
// vector_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   //vector <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.reserve( 20 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
}  
```  
  
```Output  
Current capacity of v1 = 1  
Current capacity of v1 = 20  
Current capacity of v1 = 1  
```  
  
##  <a name="a-namevectorsizea-vectorsize"></a><a name="vector__size"></a>  vector:: size  
 傳回向量中的項目數。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 向量的目前長度。  
  
### <a name="example"></a>範例  
  
```  
// vector_size.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::size_type i;  
  
   v1.push_back( 1 );  
   i = v1.size( );  
   cout << "Vector length is " << i << "." << endl;  
  
   v1.push_back( 2 );  
   i = v1.size( );  
   cout << "Vector length is now " << i << "." << endl;  
}  
```  
  
```Output  
Vector length is 1.  
Vector length is now 2.  
```  
  
##  <a name="a-namevectorsizetypea-vectorsizetype"></a><a name="vector__size_type"></a>  vector:: size_type  
 計算向量中項目數的類型。  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>範例  
  請參閱範例 [容量](#vector__capacity)。  
  
##  <a name="a-namevectorswapa-vectorswap"></a><a name="vector__swap"></a>  vector:: swap  
 交換兩個向量的項目。  
  
```  
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供待交換項目的向量，或其項目要與向量 ` left` 交換的向量。  
  
 ` left`  
 其項目要與向量 ` right` 交換的向量。  
  
### <a name="example"></a>範例  
  
```  
// vector_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1, v2;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 3 );  
  
   v2.push_back( 10 );  
   v2.push_back( 20 );  
  
   cout << "The number of elements in v1 = " << v1.size( ) << endl;  
   cout << "The number of elements in v2 = " << v2.size( ) << endl;  
   cout << endl;  
  
   v1.swap( v2 );  
  
   cout << "The number of elements in v1 = " << v1.size( ) << endl;  
   cout << "The number of elements in v2 = " << v2.size( ) << endl;  
}  
```  
  
```Output  
The number of elements in v1 = 3  
The number of elements in v2 = 2  
  
The number of elements in v1 = 2  
The number of elements in v2 = 3  
```  
  
##  <a name="a-namevectorvaluetypea-vectorvaluetype"></a><a name="vector__value_type"></a>  vector:: value_type  
 代表儲存在向量中之資料類型的類型。  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>備註  
 `value_type` 是範本參數的同義字 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// vector_value_type.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
##  <a name="a-namevectorvectora-vectorvector"></a><a name="vector__vector"></a>  vector:: vector  
 建構特定大小、具有特定值項目或具有特定配置器的向量，或將向量建構為其他一些向量的所有或部分複本。  
  
```  
vector();

explicit vector(
    const Allocator& Al);

explicit vector(
    size_type Count);

vector(
    size_type Count,  
    const Type& Val);

vector(
    size_type Count,  
    const Type& Val,  
    const Allocator& Al);

vector(
    const vector& Right);

vector(
    vector&& Right);

vector(
    initializer_list<Type> IList,  
    const _Allocator& Al);

template <class InputIterator>  
vector(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
vector(
 InputIterator First,  
    InputIterator Last,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`Al`|搭配這個物件使用的配置器類別。 [get_allocator](#vector__get_allocator) 傳回物件的配置器類別。|  
|`Count`|已建構向量中的項目數。|  
|`Val`|已建構向量中的項目值。|  
|`Right`|已建構向量為其複本的向量。|  
|`First`|項目範圍中要複製的第一個項目位置。|  
|`Last`|項目範圍之外要複製的第一個項目位置。|  
|`IList`|Initializer_list，包含要複製 elmeents。|  
  
### <a name="remarks"></a>備註  
 所有建構函式儲存配置器物件 ( `Al`) 並初始化向量。  
  
 前兩個建構函式會指定空的初始向量。 第二個明確指定的配置器類型 ( `Al`) 使用。  
  
 第三個建構函式會指定重複指定數字 ( `Count`) 的類別的預設值的項目 `Type`。  
  
 第四個和第五個建構函式指定的重複 ( `Count`) 值的項目 `Val`。  
  
 第六個建構函式會指定向量 `Right` 的複本。  
  
 第七個建構函式會移動向量 `Right`。  
  
 第八個建構函式使用 initializer_list 來指定元素。  
  
 第九個和第十個建構函式會將範圍複製 [ `First`, ，`Last`) 的向量。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_ctor.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;  
  
    // Create an empty vector v0  
    vector <int> v0;  
  
    // Create a vector v1 with 3 elements of default value 0  
    vector <int> v1(3);  
  
    // Create a vector v2 with 5 elements of value 2  
    vector <int> v2(5, 2);  
  
    // Create a vector v3 with 3 elements of value 1 and with the allocator   
    // of vector v2  
    vector <int> v3(3, 1, v2.get_allocator());  
  
    // Create a copy, vector v4, of vector v2  
    vector <int> v4(v2);  
  
    // Create a new temporary vector for demonstrating copying ranges  
    vector <int> v5(5);  
    for (auto i : v5) {  
        v5[i] = i;  
    }  
  
    // Create a vector v6 by copying the range v5[ first,  last)  
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);  
  
    cout << "v1 =";  
    for (auto& v : v1){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v2 =";  
    for (auto& v : v2){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v3 =";  
    for (auto& v : v3){  
        cout << " " << v;  
    }  
    cout << endl;  
    cout << "v4 =";  
    for (auto& v : v4){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v5 =";  
    for (auto& v : v5){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v6 =";  
    for (auto& v : v6){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    // Move vector v2 to vector v7  
    vector <int> v7(move(v2));  
    vector <int>::iterator v7_Iter;  
  
    cout << "v7 =";  
    for (auto& v : v7){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    vector<int> v8{ { 1, 2, 3, 4 } };  
    for (auto& v : v8){  
        cout << " " << v ;  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

