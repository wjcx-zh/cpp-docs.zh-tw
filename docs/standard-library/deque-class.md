---
title: "deque 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.deque"
  - "deque"
  - "std::deque"
  - "deque/std::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque 類別，關於 deque 類別"
  - "deque 類別"
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# deque 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以線性排列方式排列指定類型的項目，並且像向量一樣允許快速隨機存取任何項目，可有效率地在容器背面插入和刪除。 不過，與向量不同的是，`deque` 類別也支援在此容器前面有效率的插入和刪除。  
  
## <a name="syntax"></a>語法  
  
```unstlib  
template <class Type,   
    class Allocator =allocator<Type>>  
class deque  
```  
  
#### <a name="parameters"></a>參數  
 `Type`  
 要存放在 deque 中的項目資料類型。  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝 deque 之記憶體配置和解除配置的詳細資訊。 這個引數是選擇性的而且預設值是 **配置器 \< 類型>***。*  
  
## <a name="remarks"></a>備註  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 [向量](../standard-library/vector-class.md) 應該是慣用的容器管理序列是針對隨機存取任何項目，並插入或刪除的項目只需要在序列結尾處。 清單容器的效能會優於時有效率的插入和刪除動作序列內的任何位置 （以常數時間） 很重要。 在此序列中間的這類作業需要複製和指派項目，且和此序列中的項目數目成比例 (線性時間)。  
  
 當成員函式必須插入或清除 deque 的項目時，就會發生 deque 重新配置：  
  
-   如果項目插入空的序列，或如果將空的序列，都會清除項目，然後迭代器稍早所傳回 [開始](#deque__begin) 和 [結束](#deque__end) 會變成無效。  
  
-   如果將一個項目插入 deque 的第一個位置，則指定現有項目的所有迭代器 (而非參考) 都會變成無效。  
  
-   如果項目會插入 deque 結尾然後 [結束](#deque__end) 和所有迭代器，但沒有參考，以指定現有的項目會變成無效。  
  
-   如果在 deque 前面清除了一個項目，則只有遭清除項目的迭代器和參考會變成無效。  
  
-   如果從 deque 結尾清除了最後一個項目，則只有最後一個項目的迭代器和遭清除項目的參考會變成無效。  
  
 否則，插入或刪除一個項目會讓所有迭代器和參考失效。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[deque](#deque__deque)|建構 `deque.` 數建構函式可供設定的新內容 `deque` 不同的方式︰ 空白; 載入指定的空的項目數，內容已移動或複製從另一個 `deque`內容複製或移動是利用迭代器，而一個項目複製到 `deque`` count` 時間。 有些建構函式可使用自訂的 `allocator` 來建立項目。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#deque__allocator_type)|類型，表示 `allocator` 物件的 `deque` 類別。|  
|[const_iterator](#deque__const_iterator)|類型，提供可以存取和讀取 `deque` 中項目做為 `const` 的隨機存取迭代器。|  
|[const_pointer](#deque__const_pointer)|類型，提供 `deque` 中的項目指標做為 `const.`。|  
|[const_reference](#deque__const_reference)|類型，提供在 `deque` 中供讀取和其他作業使用之項目做為 `const.` 的參考。|  
|[const_reverse_iterator](#deque__const_reverse_iterator)|類型，提供可以存取和讀取 `deque` 中項目做為 `const` 的隨機存取迭代器。 會以反向檢視 deque。 如需詳細資訊，請參閱 [reverse_iterator 類別](../standard-library/reverse-iterator-class.md)|  
|[difference_type](#deque__difference_type)|類型，提供兩個隨機存取迭代器的差異，這些迭代器參考相同 `deque` 中的項目。|  
|[迭代器](#deque__iterator)|類型，提供隨機存取迭代器，該迭代器可讀取或修改 `deque` 中的任何項目。|  
|[指標](#deque__pointer)|類型，其提供 `deque` 中項目的指標。|  
|[參考](#deque__reference)|類型，提供儲存在 `deque` 中之項目的參考。|  
|[reverse_iterator](#deque__reverse_iterator)|類型，提供隨機存取迭代器，該迭代器可讀取或修改 `deque` 中的項目。 會以反向順序檢視 deque。|  
|[size_type](#deque__size_type)|計算 `deque` 中項目數目的類型。|  
|[value_type](#deque__value_type)|類型，表示儲存在 `deque` 中的資料類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[指派](#deque__assign)|清除 `deque` 中的項目，並複製新的項目序列至目標 `deque`。|  
|[在](#deque__at)|傳回 `deque` 中指定位置的項目參考。|  
|[上一步]](#deque__back)|傳回 `deque` 的最後一個項目的參考。|  
|[開始](#deque__begin)|傳回 `deque` 中對第一個項目定址的隨機存取迭代器。|  
|[deque:: cbegin](#deque__cbegin)|傳回 `deque` 中第一個項目的常數迭代器。|  
|[deque:: cend](#deque__cend)|傳回指向 `deque` 結尾之外的 `const` 隨機存取迭代器。|  
|[清除](#deque__clear)|清除 `deque` 的所有項目。|  
|[deque:: crbegin](#deque__crbegin)|傳回 `deque` 中以相反順序檢視之第一個項目的隨機存取常數迭代器。|  
|[deque:: crend](#deque__crend)|傳回 `deque` 中以相反順序檢視之第一個項目的隨機存取常數迭代器。|  
|[deque:: emplace](#deque__emplace)|將就地建構的項目插入 `deque` 的指定位置。|  
|[deque:: emplace_back](#deque__emplace_back)|將就地建構的項目加入 `deque` 的結尾。|  
|[deque:: emplace_front](#deque__emplace_front)|將就地建構的項目加入 `deque` 的開頭。|  
|[空白](#deque__empty)|如果 `deque` 包含零個項目，則傳回 `true`，而如果它包含一或多個項目，則傳回 `false`。|  
|[結束](#deque__end)|傳回指向 `deque` 結尾之外的隨機存取迭代器。|  
|[清除](#deque__erase)|從指定位置移除在 `deque` 中的項目或某個項目範圍。|  
|[前端](#deque__front)|傳回 `deque` 中第一個項目的參考。|  
|[get_allocator](#deque__get_allocator)|傳回用來建構 `allocator` 的 `deque` 物件複本。|  
|[插入](#deque__insert)|將一個項目、多個項目或一定範圍的項目在指定位置插入 `deque`。|  
|[max_size](#deque__max_size)|傳回 `deque` 的最大可能長度。|  
|[pop_back](#deque__pop_back)|清除 `deque` 結尾的項目。|  
|[pop_front](#deque__pop_front)|清除 `deque` 開頭的項目。|  
|[push_back](#deque__push_back)|將項目加入 `deque` 的結尾。|  
|[push_front](#deque__push_front)|將項目加入 `deque` 的開頭。|  
|[rbegin](#deque__rbegin)|傳回反轉的 `deque` 中第一個項目的隨機存取迭代器。|  
|[rend](#deque__rend)|傳回在反轉的 `deque` 中恰好指向最後一個項目之外的隨機存取迭代器。|  
|[調整大小](#deque__resize)|指定 `deque` 的新大小。|  
|[deque:: shrink_to_fit](#deque__shrink_to_fit)|捨棄多餘的容量。|  
|[大小](#deque__size)|傳回 `deque` 中項目的數目。|  
|[交換](#deque__swap)|交換兩個 `deque` 的項目。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 &#91; & #93。](#deque__operator_at)|傳回在指定位置上 `deque` 項目的參考。|  
|[deque:: =](#deque__operator_eq)|用另一個 `deque` 的複本取代 `deque` 的項目。|  
  
## <a name="requirements"></a>需求  
 **標頭**: \< q u>  
  
##  <a name="a-namedequeallocatortypea-dequeallocatortype"></a><a name="deque__allocator_type"></a>  deque:: allocator_type  
 Deque 物件的配置器類別表示的型別。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 **allocator_type** 是範本參數的同義字 **配置器**。  
  
### <a name="example"></a>範例  
  請參閱範例 [get_allocator](#deque__get_allocator)。  
  
##  <a name="a-namedequeassigna-dequeassign"></a><a name="deque__assign"></a>  deque:: assign  
 清除 deque 中的項目，並將一組新的項目複製到目標 q u。  
  
```  
template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);

void assign(
    size_type Count,  
    const Type& Val);

void assign(
    initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>參數  
 `First`  
 從引數 deque 複製的項目範圍中的第一個項目位置。  
  
 `Last`  
 從引數 deque 複製的項目範圍之外的第一個項目位置。  
  
 `Count`  
 Deque 插入的項目複本數目。  
  
 `Val`  
 Deque 插入項目的值。  
  
 `IList`  
 要插入至 deque initializer_list。  
  
### <a name="remarks"></a>備註  
 會清除目標 deque 中的任何現有項目之後， `assign` 插入指定的項目範圍從原始 deque 或某些其他 deque 目標 q u 或指定值的新項目複本插入目標 q u。  
  
### <a name="example"></a>範例  
  
```  
// deque_assign.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <initializer_list>  
  
int main()  
{  
    using namespace std;  
    deque <int> c1, c2;  
    deque <int>::const_iterator cIter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    deque<int> d1{ 1, 2, 3, 4 };  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    d1.assign(iList);  
  
    cout << "d1 = ";  
    for (int i : d1)  
        cout << i;  
    cout << endl;  
  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(++c2.begin(), c2.end());  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(7, 4);  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
}  
  
```  
  
```Output  
d1 = 5678c1 =102030c1 =5060c1 =4444444  
```  
  
##  <a name="a-namedequeata-dequeat"></a><a name="deque__at"></a>  deque:: at  
 傳回指定之位置處的項目中參考 deque。  
  
```  
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 註標 （或位置編號） 的項目 q u 中參考。  
  
### <a name="return-value"></a>傳回值  
 如果 `_Pos` deque 大小大於 **在** 擲回例外狀況。  
  
### <a name="return-value"></a>傳回值  
 如果傳回值 **在** 指派給 `const_reference`, ，不能修改 deque 物件。 如果傳回值 **在** 指派給 **參考**, ，可以修改 deque 物件。  
  
### <a name="example"></a>範例  
  
```  
// deque_at.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int& i = c1.at( 0 );  
   int& j = c1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequebacka-dequeback"></a><a name="deque__back"></a>  deque:: back  
 傳回 deque 的最後一個元素的參考。  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>傳回值  
 Deque 最後一個項目。 如果 q u 是空的則傳回值會是未定義。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **回** 指派給 `const_reference`, ，不能修改 deque 物件。 如果傳回值 **回** 指派給 **參考**, ，可以修改 deque 物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空的 deque 中的項目，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// deque_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.back( );  
   const int& ii = c1.front( );  
  
   cout << "The last integer of c1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The last integer of c1 is 11  
The next-to-last integer of c1 is 10  
```  
  
##  <a name="a-namedequebegina-dequebegin"></a><a name="deque__begin"></a>  deque:: begin  
 傳回迭代器定址 deque 中的第一個項目。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>傳回值  
 隨機存取迭代器 deque 或下一個位置定址空白 deque 的第一個項目定址。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **開始** 指派給 `const_iterator`, ，不能修改 deque 物件。 如果傳回值 **開始** 指派給 **迭代器**, ，可以修改 deque 物件。  
  
### <a name="example"></a>範例  
  
```  
// deque_begin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::const_iterator c1_cIter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is " << *c1_Iter << endl;  
  
 *c1_Iter = 20;  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is now " << *c1_Iter << endl;  
  
   // The following line would be an error because iterator is const  
   // *c1_cIter = 200;  
}  
```  
  
```Output  
The first element of c1 is 1  
The first element of c1 is now 20  
```  
  
##  <a name="a-namedequecbegina-dequecbegin"></a><a name="deque__cbegin"></a>  deque:: cbegin  
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
  
##  <a name="a-namedequecenda-dequecend"></a><a name="deque__cend"></a>  deque:: cend  
 傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 指向範圍結尾之外的隨機存取迭代器。  
  
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
  
##  <a name="a-namedequecleara-dequeclear"></a><a name="deque__clear"></a>  deque:: clear  
 清除所有的項目 q u。  
  
```  
void clear();
```  
  
### <a name="example"></a>範例  
  
```  
// deque_clear.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "The size of the deque is initially " << c1.size( ) << endl;  
   c1.clear( );  
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;  
}  
```  
  
```Output  
The size of the deque is initially 3  
The size of the deque after clearing is 0  
```  
  
##  <a name="a-namedequeconstiteratora-dequeconstiterator"></a><a name="deque__const_iterator"></a>  deque:: const_iterator  
 類型，提供隨機存取迭代器可以存取和讀取 **const** deque 中的項目。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_iterator` 無法用來修改元素的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [回](#deque__back)。  
  
##  <a name="a-namedequeconstpointera-dequeconstpointer"></a><a name="deque__const_pointer"></a>  deque:: const_pointer  
 提供的指標 `const` deque 中的項目。  
  
```unstlib  
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_pointer` 無法用來修改元素的值。  [迭代器](#deque__iterator) 通常用來存取 deque 項目。  
  
##  <a name="a-namedequeconstreferencea-dequeconstreference"></a><a name="deque__const_reference"></a>  deque:: const_reference  
 提供的參考型別 **const** 項目儲存在供讀取和執行 deque **const** 作業。  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>備註  
 類型 `const_reference` 無法用來修改元素的值。  
  
### <a name="example"></a>範例  
  
```  
// deque_const_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const deque <int> c2 = c1;  
   const int &i = c2.front( );  
   const int &j = c2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as c2 is const  
   // c2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequeconstreverseiteratora-dequeconstreverseiterator"></a><a name="deque__const_reverse_iterator"></a>  deque:: const_reverse_iterator  
 類型，提供隨機存取迭代器可以讀取任何 **const** deque 中的項目。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 型別 `const_reverse_iterator` 無法修改項目的值，且用來逐一查看反轉 deque。  
  
### <a name="example"></a>範例  
  請參閱範例 [rbegin](#deque__rbegin) 如需如何宣告和使用迭代器的範例。  
  
##  <a name="a-namedequecrbegina-dequecrbegin"></a><a name="deque__crbegin"></a>  deque:: crbegin  
 傳回常數迭代器反轉 deque 中的第一個項目。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反向隨機存取迭代器定址反轉的第一個元件 [deque](../standard-library/deque-class.md) 或定址為未反轉的最後一個元素 `deque`。  
  
### <a name="remarks"></a>備註  
 有 `crbegin` 的傳回值時，無法修改 `deque` 物件。  
  
### <a name="example"></a>範例  
  
```  
// deque_crbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator v1_Iter;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of deque is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed deque is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of deque is 1.  
The first element of the reversed deque is 2.  
```  
  
##  <a name="a-namedequecrenda-dequecrend"></a><a name="deque__crend"></a>  deque:: crend  
 傳回一個位置定址反轉 deque 的最後一個元素的 const 迭代器。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 常數反向隨機存取迭代器定址反轉的最後一個元素的位置， [deque](../standard-library/deque-class.md) （有前面加上反轉 deque 中的第一個項目位置）。  
  
### <a name="remarks"></a>備註  
 `crend` 使用與反轉 `deque` 就像 [array::cend](../standard-library/array-class-stl.md#array__cend) 搭配 `deque`。  
  
 傳回的值是 `crend` （適當遞減）， `deque` 無法修改物件。  
  
 `crend` 可用來測試反轉迭代器是否已到達其 deque 結尾。  
  
 `crend` 所傳回的值不應該取值。  
  
### <a name="example"></a>範例  
  
```  
// deque_crend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
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
  
##  <a name="a-namedequedequea-dequedeque"></a><a name="deque__deque"></a>  deque:: deque  
 建構特定大小，或具有特定值，或具有特定配置器，或複製的所有或部分的其他 q u 的項目 q u。  
  
```  
deque();

explicit deque(
    const Allocator& Al);

explicit deque(
    size_type Count);

deque(
    size_type Count,  
    const Type& Val);

deque(
    size_type Count,  
    const Type& Val,  
    const Allocator& Al);

deque(
    const deque& Right);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last,  
    const Allocator& Al);

deque(
    initializer_list<value_type>  
IList,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`Al`|搭配這個物件使用的配置器類別。|  
|`Count`|建構 deque 中項目的數目。|  
|`Val`|建構 deque 中項目的值。|  
|`Right`|Deque 建構的 deque 是有要複製。|  
|`First`|項目範圍中要複製的第一個項目位置。|  
|`Last`|項目範圍之外要複製的第一個項目位置。|  
|`IList`|要複製 initializer_list。|  
  
### <a name="remarks"></a>備註  
 所有建構函式儲存配置器物件 ( `Al`) 並初始化 q u。  
  
 前兩個建構函式指定空的初始 deque;第二個也會指定配置器類型 ( `_Al`) 使用。  
  
 第三個建構函式會指定重複指定數字 ( ` count`) 的類別的預設值的項目 `Type`。  
  
 第四個和第五個建構函式指定的重複 ( `Count`) 值的項目 ` val`。  
  
 第六個建構函式會指定一份 deque `Right`。  
  
 第七個和第八個建構函式會將範圍複製 `[First, Last)` deque。  
  
 第七個建構函式移 deque `Right`。  
  
 第八個建構函式複製 initializer_list 的內容。  
  
 沒有建構函式會執行任何暫時重新配置。  
  
### <a name="example"></a>範例  
  
```  
/ compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <forward_list>  
  
int main()  
{  
    using namespace std;  
  
    forward_list<int> f1{ 1, 2, 3, 4 };  
  
    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });  
  
    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1(3);  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2(5, 2);  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3(3, 1, c2.get_allocator());  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4(c2);  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5(c4.begin(), c4_Iter);  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for (int i : c1)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for (int i : c2)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for (int i : c3)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for (int i : c4)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for (int i : c5)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for (int i : c6)  
        cout << i << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7(move(c6));  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =";  
    for (int i : c7)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    for (int i : c9)  
        cout << i << " ";  
    cout << endl;  
  
    int x = 3;  
}  
// deque_deque.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
    using namespace std;  
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1( 3 );  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2( 5, 2 );  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3( 3, 1, c2.get_allocator( ) );  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4( c2 );  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin( );  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5( c4.begin( ), c4_Iter );  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin( );  
   c4_Iter++;  
   c4_Iter++;  
   c4_Iter++;  
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
        initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
        cout << *c1_Iter << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
        cout << *c2_Iter << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
        cout << *c3_Iter << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )  
        cout << *c4_Iter << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )  
        cout << *c5_Iter << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )  
        cout << *c6_Iter << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7( move(c6) );  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =" ;  
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )  
        cout << " " << *c7_Iter;  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    or (int i : c9)  
        cout << i << " ";  
    cout << endl;  
}  
```  
  
##  <a name="a-namedequedifferencetypea-dequedifferencetype"></a><a name="deque__difference_type"></a>  deque:: difference_type  
 類型，提供兩個參考相同的 deque 內項目的迭代器之間的差異。  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 `difference_type` 也可以兩個指標之間的項目數來描述。  
  
### <a name="example"></a>範例  
  
```  
// deque_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <deque>  
#include <algorithm>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   deque <int>::difference_type df_typ1, df_typ2, df_typ3;  
  
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
  
##  <a name="a-namedequeemplacea-dequeemplace"></a><a name="deque__emplace"></a>  deque:: emplace  
 插入的指定位置 deque 就地建構的項目。  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`_Where`|中的位置 [deque](../standard-library/deque-class.md) 插入的第一個元素的位置。|  
|` val`|插入 `deque` 的項目值。|  
  
### <a name="return-value"></a>傳回值  
 函數會傳回迭代器指向新的項目插入至 deque 其中的位置。  
  
### <a name="remarks"></a>備註  
 任何插入作業都可能高度耗費資源，請參閱 `deque` 的討論 `deque` 效能。  
  
### <a name="example"></a>範例  
  
```  
// deque_emplace.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
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
  
##  <a name="a-namedequeemplacebacka-dequeemplaceback"></a><a name="deque__emplace_back"></a>  deque:: emplace_back  
 將結尾 deque 就地建構的項目。  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` val`|將元素加入至結尾 [deque](../standard-library/deque-class.md)。|  
  
### <a name="example"></a>範例  
  
```  
// deque_emplace_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_back( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemplacefronta-dequeemplacefront"></a><a name="deque__emplace_front"></a>  deque:: emplace_front  
 將結尾 deque 就地建構的項目。  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` val`|加入開頭的項目 [deque](../standard-library/deque-class.md)。|  
  
### <a name="example"></a>範例  
  
```  
// deque_emplace_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_front( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemptya-dequeempty"></a><a name="deque__empty"></a>  deque:: empty  
 測試是否 q u 是空的。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 **true** q u 是空的; 如果 **false** 如果 deque 不是空白。  
  
### <a name="example"></a>範例  
  
```  
// deque_empty.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   if ( c1.empty( ) )  
      cout << "The deque is empty." << endl;  
   else  
      cout << "The deque is not empty." << endl;  
}  
```  
  
```Output  
The deque is not empty.  
```  
  
##  <a name="a-namedequeenda-dequeend"></a><a name="deque__end"></a>  deque:: end  
 傳回迭代器位置定址 deque 中的最後一個項目。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>傳回值  
 隨機存取迭代器位置定址 deque 中的最後一個項目。 如果 q u 是空的則 deque:: end = = deque。  
  
### <a name="remarks"></a>備註  
 **結束** 用來測試是否迭代器已達到其 deque 結尾。  
  
### <a name="example"></a>範例  
  
```  
// deque_end.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_Iter = c1.end( );  
   c1_Iter--;  
   cout << "The last integer of c1 is " << *c1_Iter << endl;  
  
   c1_Iter--;  
 *c1_Iter = 400;  
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;  
  
   // If a const iterator had been declared instead with the line:  
   // deque <int>::const_iterator c1_Iter;  
   // an error would have resulted when inserting the 400  
  
   cout << "The deque is now:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
}  
```  
  
```Output  
The last integer of c1 is 30  
The new next-to-last integer of c1 is 400  
The deque is now: 10 400 30  
```  
  
##  <a name="a-namedequeerasea-dequeerase"></a><a name="deque__erase"></a>  deque:: erase  
 移除項目或項目範圍中的指定位置的 deque。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>參數  
 `_Where`  
 要從 deque 移除項目的位置。  
  
 ` first`  
 從 deque 移除第一個項目的位置。  
  
 ` last`  
 從 deque 移除最後一個元素之後的位置。  
  
### <a name="return-value"></a>傳回值  
 將指定的任何項目移除，剩餘的第一個元素的隨機存取迭代器或 deque 如果沒有這類項目結尾的指標。  
  
### <a name="remarks"></a>備註  
 如需有關 **清除**, ，請參閱 [deque:: erase 和 deque:: clear](../misc/deque-erase-and-deque-clear.md)。  
  
 **清除** 絕不會擲回例外狀況。  
  
### <a name="example"></a>範例  
  
```  
// deque_erase.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 40 );  
   c1.push_back( 50 );  
   cout << "The initial deque is: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   c1.erase( c1.begin( ) );  
   cout << "After erasing the first element, the deque becomes:  ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   Iter = c1.begin( );  
   Iter++;  
   c1.erase( Iter, c1.end( ) );  
   cout << "After erasing all elements but the first, deque becomes: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The initial deque is: 10 20 30 40 50   
After erasing the first element, the deque becomes:  20 30 40 50   
After erasing all elements but the first, deque becomes: 20   
```  
  
##  <a name="a-namedequefronta-dequefront"></a><a name="deque__front"></a>  deque:: front  
 Deque 中傳回的第一個元素的參考。  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 q u 是空的傳回為未定義。  
  
### <a name="remarks"></a>備註  
 如果傳回值 `front` 指派給 `const_reference`, ，不能修改 deque 物件。 如果傳回值 `front` 指派給 **參考**, ，可以修改 deque 物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空的 deque 中的項目，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// deque_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.front( );  
   const int& ii = c1.front( );  
  
   cout << "The first integer of c1 is " << i << endl;  
   i++;  
   cout << "The second integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 11  
```  
  
##  <a name="a-namedequegetallocatora-dequegetallocator"></a><a name="deque__get_allocator"></a>  deque:: get_allocator  
 傳回用來建構 deque 的配置器物件複本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 Deque 使用的配置器。  
  
### <a name="remarks"></a>備註  
 Deque 類別配置器指定類別如何管理儲存體。 預設配置器所提供的STL 容器類別，已足夠大多數的程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。  
  
### <a name="example"></a>範例  
  
```  
// deque_get_allocator.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   deque <int> c1;  
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );  
  
   // c3 will use the same allocator class as c1  
   deque <int> c3( c1.get_allocator( ) );  
  
   deque <int>::allocator_type xlst = c1.get_allocator( );  
   // You can now call functions on the allocator class used by c1  
}  
```  
  
##  <a name="a-namedequeinserta-dequeinsert"></a><a name="deque__insert"></a>  deque:: insert  
 將某個元素或一些元素或某個項目範圍插入位於指定位置 q u。  
  
```  
iterator insert(
    const_iterator Where,  
    const Type& Val);

iterator insert(
    const_iterator Where,  
    Type&& Val);

void insert(
    iterator Where,  
    size_type Count,  
    const Type& Val);

template <class InputIterator>  
void insert(
    iterator Where,  
    InputIterator First,  
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Where`|目標 deque 中插入的第一個元素的位置。|  
|`Val`|Deque 插入項目的值。|  
|`Count`|Deque 插入的項目數目。|  
|`First`|要複製的引數 deque 中的項目範圍中第一個項目的位置。|  
|`Last`|要複製的引數 deque 中的項目範圍之外的第一個項目位置。|  
|`IList`|要插入項目的 initializer_list。|  
  
### <a name="return-value"></a>傳回值  
 前兩個插入函式會傳回迭代器指向新的項目插入至 deque 其中的位置。  
  
### <a name="remarks"></a>備註  
 任何插入作業可能相當昂貴。  
  
##  <a name="a-namedequeiteratora-dequeiterator"></a><a name="deque__iterator"></a>  deque:: iterator  
 類型，提供隨機存取迭代器可以讀取或修改 deque 中的任何項目。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>備註  
 型別 **迭代器** 可以用來修改項目的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [開始](#deque__begin)。  
  
##  <a name="a-namedequemaxsizea-dequemaxsize"></a><a name="deque__max_size"></a>  deque:: max_size  
 傳回 deque 的最大長度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 Deque 最大可能長度。  
  
### <a name="example"></a>範例  
  
```  
// deque_max_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   i = c1.max_size( );  
   cout << "The maximum possible length of the deque is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namedequeoperatorata-dequeoperator"></a><a name="deque__operator_at"></a>  deque:: operator]  
 傳回位於指定位置 deque 項目的參考。  
  
```  
reference operator[](size_type _Pos);

const_reference operator[](size_type _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 Deque 項目參考位置。  
  
### <a name="return-value"></a>傳回值  
 引數中指定其位置的項目參考。 如果指定的位置大於 deque 的大小，則結果會是未定義。  
  
### <a name="remarks"></a>備註  
 如果傳回值 `operator[]` 指派給 `const_reference`, ，不能修改 deque 物件。 如果傳回值 `operator[]` 指派給 **參考**, ，可以修改 deque 物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取 deque 界限之外的項目，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// deque_op_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   cout << "The first integer of c1 is " << c1[0] << endl;  
   int& i = c1[1];  
   cout << "The second integer of c1 is " << i << endl;  
  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 20  
```  
  
##  <a name="a-namedequeoperatoreqa-dequeoperator"></a><a name="deque__operator_eq"></a>  deque:: =  
 取代使用項目從另一個 deque 這個 deque 的項目。  
  
```  
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` right`|Deque 提供新的內容。|  
  
### <a name="remarks"></a>備註  
 第一個覆寫項目複製到從這個 deque ` right`, ，作業的來源。 第二個覆寫會將項目移至 [從這個 deque ` right`。  
  
 運算子執行之前，此 deque 中所包含的項目被移除。  
  
### <a name="example"></a>範例  
  
```  
// deque_operator_as.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
using namespace std;  
  
typedef deque<int> MyDeque;  
  
template<typename MyDeque> struct S;  
  
template<typename MyDeque> struct S<MyDeque&> {  
  static void show( MyDeque& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
    cout << endl;  
  }  
};  
  
template<typename MyDeque> struct S<MyDeque&&> {  
  static void show( MyDeque&& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
cout << " via unnamed rvalue reference " << endl;  
  }  
};  
  
int main( )  
{  
   MyDeque d1, d2;  
  
   d1.push_back(10);  
   d1.push_back(20);  
   d1.push_back(30);  
   d1.push_back(40);  
   d1.push_back(50);  
  
   cout << "d1 = " ;  
   S<MyDeque&>::show( d1 );  
  
   d2 = d1;  
   cout << "d2 = ";  
   S<MyDeque&>::show( d2 );  
  
   cout << "     ";  
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );  
 }  
```  
  
##  <a name="a-namedequepointera-dequepointer"></a><a name="deque__pointer"></a>  deque:: pointer  
 提供的指標中的項目 [deque](../standard-library/deque-class.md)。  
  
```unstlib  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 型別 **指標** 可以用來修改項目的值。  [迭代器](#deque__iterator) 通常用來存取 deque 項目。  
  
##  <a name="a-namedequepopbacka-dequepopback"></a><a name="deque__pop_back"></a>  deque:: pop_back  
 刪除 deque 結尾處的項目。  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>備註  
 最後一個項目不能是空的。 `pop_back` 絕不會擲回例外狀況。  
  
### <a name="example"></a>範例  
  
```  
// deque_pop_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The last element is: " << c1.back( ) << endl;  
  
   c1.pop_back( );  
   cout << "After deleting the element at the end of the deque, the "  
      "last element is: " << c1.back( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The last element is: 2  
After deleting the element at the end of the deque, the last element is: 1  
```  
  
##  <a name="a-namedequepopfronta-dequepopfront"></a><a name="deque__pop_front"></a>  deque:: pop_front  
 刪除 q u 的開頭處的項目。  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>備註  
 第一個項目不能空白。 `pop_front` 絕不會擲回例外狀況。  
  
### <a name="example"></a>範例  
  
```  
// deque_pop_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The second element is: " << c1.back( ) << endl;  
  
   c1.pop_front( );  
   cout << "After deleting the element at the beginning of the "  
      "deque, the first element is: " << c1.front( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The second element is: 2  
After deleting the element at the beginning of the deque, the first element is: 2  
```  
  
##  <a name="a-namedequepushbacka-dequepushback"></a><a name="deque__push_back"></a>  deque:: push_back  
 將元素加入至 deque 結尾。  
  
```  
void push_back(const Type& val);

void push_back(Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` val`|Deque 的結尾處加入項目。|  
  
### <a name="remarks"></a>備註  
 如果擲回例外狀況，deque 會保持不變，並重新擲回例外狀況。  
  
##  <a name="a-namedequepushfronta-dequepushfront"></a><a name="deque__push_front"></a>  push_front  
 將元素加入至 q u 的開頭。  
  
```  
    void push_front(const Type& val);

void push_front(Type&& val);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` val`|Q u 的開頭加入的項目。|  
  
### <a name="remarks"></a>備註  
 如果擲回例外狀況，deque 會保持不變，並重新擲回例外狀況。  
  
### <a name="example"></a>範例  
  
```  
// deque_push_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_front( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "First element: " << c1.front( ) << endl;  
  
   c1.push_front( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New first element: " << c1.front( ) << endl;  
  
// move initialize a deque of strings  
   deque <string> c2;  
   string str("a");  
  
   c2.push_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
First element: 1  
New first element: 2  
Moved first element: a  
```  
  
##  <a name="a-namedequerbegina-dequerbegin"></a><a name="deque__rbegin"></a>  deque:: rbegin  
 傳回迭代器反轉 deque 中的第一個項目。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>傳回值  
 反向隨機存取迭代器定址反轉 deque 中的第一個項目，或為未反轉 deque 中的最後一個項目定址。  
  
### <a name="remarks"></a>備註  
 `rbegin` 用於反轉 deque 就像 [開始](#deque__begin) deque 搭配使用。  
  
 如果傳回值 `rbegin` 指派給 `const_reverse_iterator`, ，不能修改 deque 物件。 如果傳回值 `rbegin` 指派給 `reverse_iterator`, ，可以修改 deque 物件。  
  
 `rbegin` 可用來向後逐一查看 q u。  
  
### <a name="example"></a>範例  
  
```  
// deque_rbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
  
   // If the following line had replaced the line above, an error   
   // would have resulted in the line modifying an element   
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rbegin( );  
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;  
  
   cout << "The deque contains the elements: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << "in that order.";  
   cout << endl;  
  
   // rbegin can be used to iterate through a deque in reverse order  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rbegin( );  
 *c1_rIter = 40;  // This would have caused an error if a   
                    // const_reverse iterator had been declared as   
                    // noted above  
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;  
}  
```  
  
```Output  
Last element in the deque is 30.  
The deque contains the elements: 10 20 30 in that order.  
The reversed deque is: 30 20 10   
Last element in deque is now 40.  
```  
  
##  <a name="a-namedequereferencea-dequereference"></a><a name="deque__reference"></a>  deque:: reference  
 類型，提供儲存在 deque 項目的參考。  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>範例  
  
```  
// deque_reference.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int &i = c1.front( );  
   int &j = c1.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequerenda-dequerend"></a><a name="deque__rend"></a>  deque:: rend  
 傳回迭代器位置定址反轉 deque 中的最後一個項目。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>傳回值  
 反向隨機存取迭代器位置定址反轉 deque （有前面加上反轉 deque 中的第一個項目位置） 中的最後一個項目。  
  
### <a name="remarks"></a>備註  
 `rend` 用於反轉 deque 就像 [結束](#deque__end) deque 搭配使用。  
  
 如果傳回值 `rend` 指派給 `const_reverse_iterator`, ，不能修改 deque 物件。 如果傳回值 `rend` 指派給 `reverse_iterator`, ，可以修改 deque 物件。  
  
 `rend` 可用來測試是否反向迭代器已達到其 deque 結尾。  
  
 `rend` 所傳回的值不應該取值。  
  
### <a name="example"></a>範例  
  
```  
// deque_rend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
   // If the following line had replaced the line above, an error  
   // would have resulted in the line modifying an element  
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rend( );  
   c1_rIter --; // Decrementing a reverse iterator moves it forward   
                // in the deque (to point to the first element here)  
   cout << "The first element in the deque is: " << *c1_rIter << endl;  
  
   cout << "The deque is: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << endl;  
  
   // rend can be used to test if an iteration is through all of   
   // the elements of a reversed deque  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rend( );  
   c1_rIter--; // Decrementing the reverse iterator moves it backward   
               // in the reversed deque (to the last element here)  
 *c1_rIter = 40; // This modification of the last element would   
                   // have caused an error if a const_reverse   
                   // iterator had been declared (as noted above)  
   cout << "The modified reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The first element in the deque is: 10  
The deque is: 10 20 30   
The reversed deque is: 30 20 10   
The modified reversed deque is: 30 20 40   
```  
  
##  <a name="a-namedequeresizea-dequeresize"></a><a name="deque__resize"></a>  deque:: resize  
 指定 deque 的新大小。  
  
```  
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>參數  
 `_Newsize`  
 Deque 新的大小。  
  
 ` val`  
 如果新的大小大於 deque 加入新項目值的原始大小。 如果省略此值，則新的項目會指定類別的預設值。  
  
### <a name="remarks"></a>備註  
 Deque 大小小於所要求的大小，如果 `_Newsize`, ，元素會加入至 deque，直到達到所要求的大小。  
  
 Deque 達到大小之前，如果 deque 大小大於所要求的大小，會刪除最接近 deque 結尾的項目 `_Newsize`。  
  
 如果現在 deque 的大小與所要求的大小相同，會不採取任何動作。  
  
 [大小](#deque__size) 反映 deque 的目前大小。  
  
### <a name="example"></a>範例  
  
```  
// deque_resize.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{   
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1.resize( 4,40 );  
   cout << "The size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is " << c1.back( ) << endl;  
  
   c1.resize( 5 );  
   cout << "The size of c1 is now: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
  
   c1.resize( 2 );  
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
}  
```  
  
```Output  
The size of c1 is: 4  
The value of the last element is 40  
The size of c1 is now: 5  
The value of the last element is now 0  
The reduced size of c1 is: 2  
The value of the last element is now 20  
```  
  
##  <a name="a-namedequereverseiteratora-dequereverseiterator"></a><a name="deque__reverse_iterator"></a>  deque:: reverse_iterator  
 類型，提供隨機存取迭代器可以讀取或修改反轉 deque 中的項目。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 型別 `reverse_iterator` 用來逐一查看 q u。  
  
### <a name="example"></a>範例  
  請參閱 rbegin 的範例。  
  
##  <a name="a-namedequeshrinktofita-dequeshrinktofit"></a><a name="deque__shrink_to_fit"></a>  deque:: shrink_to_fit  
 捨棄多餘的容量。  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>備註  
 沒有任何可攜式方法，以判斷 `shrink_to_fit` 可減少使用的儲存體 [deque](../standard-library/deque-class.md)。  
  
### <a name="example"></a>範例  
  
```  
// deque_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   //deque <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
}  
```  
  
```Output  
Current size of v1 = 1  
Current size of v1 = 1  
```  
  
##  <a name="a-namedequesizea-dequesize"></a><a name="deque__size"></a>  deque:: size  
 Deque 中傳回的項目數。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 Deque 目前的長度。  
  
### <a name="example"></a>範例  
  
```  
// deque_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   c1.push_back( 1 );  
   i = c1.size( );  
   cout << "The deque length is " << i << "." << endl;  
  
   c1.push_back( 2 );  
   i = c1.size( );  
   cout << "The deque length is now " << i << "." << endl;  
}  
```  
  
```Output  
The deque length is 1.  
The deque length is now 2.  
```  
  
##  <a name="a-namedequesizetypea-dequesizetype"></a><a name="deque__size_type"></a>  deque:: size_type  
 計算 deque 中的項目數的類型。  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>範例  
  請參閱範例 [大小](#deque__size)。  
  
##  <a name="a-namedequeswapa-dequeswap"></a><a name="deque__swap"></a>  deque:: swap  
 交換兩個 deque 的項目。  
  
```  
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>  
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供待交換時，項目 q u 或其項目要交換與 deque deque ` left`。  
  
 ` left`  
 其項目要交換與 deque deque ` right`。  
  
### <a name="example"></a>範例  
  
```  
// deque_swap.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2, c3;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 3 );  
   c2.push_back( 10 );  
   c2.push_back( 20 );  
   c3.push_back( 100 );  
  
   cout << "The original deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.swap( c2 );  
  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap( c1,c3 );  
  
   cout << "After swapping with c3, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap<>(c1, c2);  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original deque c1 is: 1 2 3  
After swapping with c2, deque c1 is: 10 20  
After swapping with c3, deque c1 is: 100  
After swapping with c2, deque c1 is: 1 2 3  
```  
  
##  <a name="a-namedequevaluetypea-dequevaluetype"></a><a name="deque__value_type"></a>  deque:: value_type  
 表示在 deque 中儲存的資料類型的類型。  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>備註  
 `value_type` 是範本參數的同義字 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// deque_value_type.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   deque<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

