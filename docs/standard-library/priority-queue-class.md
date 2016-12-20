---
title: "priority_queue 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.priority_queue"
  - "priority_queue"
  - "std::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "priority_queue 類別"
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# priority_queue 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範本容器配接器類別，提供的功能限制的存取權的一些基礎的容器類型，都是最大或最高優先順序的最上層元素的限制。 Priority_queue 可以加入新項目，可以檢查或移除 priority_queue 頂端的項目。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>  
class priority_queue  
```  
  
#### <a name="parameters"></a>參數  
 *Type*  
 Priority_queue 中儲存項目資料型別。  
  
 `Container`  
 用來實作 priority_queue 基礎容器的類型。  
  
 *比較*  
 提供的函式物件的型別可以比較兩個項目值做為排序鍵，以判斷 priority_queue 中的相對順序。 這個引數是選擇性的二元述詞和 **小於***\<***typename** *容器***:: value_type***>* 做為預設值。  
  
## <a name="remarks"></a>備註  
 類別的項目 **類型** 約定第一個範本中的佇列物件的參數是同義詞 [value_type](#priority_queue__value_type) ，而且必須符合基礎容器類別中的項目類型 **容器** 約定由第二個範本參數。  **類型** 必須指派，如此就可以複製該類型的物件，並將值指派給該型別的變數。  
  
 Priority_queue 訂單藉由呼叫類別的預存函式物件所控制的序列 **特性**。 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  
  
 包含適合基礎容器類別，如 priority_queue [deque 類別](../standard-library/deque-class.md) 和預設 [vector 類別](../standard-library/vector-class.md) 或任何其他支援的作業序列容器 `front`, ，`push_back`, ，和 `pop_back` 和隨機存取迭代器。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。  
  
 將項目來加入和移除項目從 `priority_queue` 兩者都有對數的複雜性。 存取項目中的 `priority_queue` 有常數複雜度。  
  
 有三種類型的 STL 所定義的容器配接器︰ 堆疊、 佇列和 priority_queue。 每個會限制一些基礎容器類別，以提供標準的資料結構的精確地控制的介面的功能。  
  
-    [Stack 類別](../standard-library/stack-class.md) 支援後進先出 (LIFO) 資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。  
  
-    [Queue 類別](../standard-library/queue-class.md) 支援先進先出 (FIFO) 資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制存取只正面和背面元素以這種方式是使用佇列類別的原因。  
  
-   Priority_queue 類別排序其項目，因此，最大項目會一直在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[priority_queue](#priority_queue__priority_queue)|建構 `priority_queue` 也就是空的或，是一份基底的容器物件或另一個範圍 `priority_queue`。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#priority_queue__container_type)|提供基底容器以讓 `priority_queue` 調整的類型。|  
|[size_type](#priority_queue__size_type)|不帶正負號的整數類型，可以表示 `priority_queue` 中的項目數。|  
|[value_type](#priority_queue__value_type)|此類型代表儲存為 `priority_queue` 項目的物件類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[空白](#priority_queue__empty)|測試 `priority_queue` 是否為空白。|  
|[快顯](#priority_queue__pop)|移除的最大項目 `priority_queue` 從頂端的位置。|  
|[推播](#priority_queue__push)|將元素加入至根據優先順序的運算子中的項目優先權佇列 <。|  
|[大小](#priority_queue__size)|傳回 `priority_queue` 中項目的數目。|  
|[頁首](#priority_queue__top)|傳回常數參考的最大的項目上方的 `priority_queue`。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 佇列>  
  
 **命名空間：** std  
  
##  <a name="a-namepriorityqueuecontainertypea-priorityqueuecontainertype"></a><a name="priority_queue__container_type"></a>  priority_queue:: container_type  
 提供基底的容器必須採用型別。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是樣板參數 `Container` 的同義字。 STL 序列容器類別 deque 和預設類別向量符合的需求來做為 priority_queue 物件的基底的容器。 也可能使用滿足需求的使用者定義型別。  
  
 如需有關 `Container`, ，請參閱 \< 備註 > 一節 [priority_queue 類別](../standard-library/priority-queue-class.md) 主題。  
  
### <a name="example"></a>範例  
  請參閱範例 [priority_queue](#priority_queue__priority_queue) 如需如何宣告和使用的範例 `container_type`。  
  
##  <a name="a-namepriorityqueueemptya-priorityqueueempty"></a><a name="priority_queue__empty"></a>  priority_queue:: empty  
 測試是否 priority_queue 是空的。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 **true** priority_queue 是空的; 如果 **false** 如果 priority_queue 是空的。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue <int> q1, s2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The priority_queue q1 is empty." << endl;  
   else  
      cout << "The priority_queue q1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The priority_queue s2 is empty." << endl;  
   else  
      cout << "The priority_queue s2 is not empty." << endl;  
}  
```  
  
```Output  
The priority_queue q1 is not empty.  
The priority_queue s2 is empty.  
```  
  
##  <a name="a-namepriorityqueuepopa-priorityqueuepop"></a><a name="priority_queue__pop"></a>  priority_queue:: pop  
 從頂端位置移除 priority_queue 最大項目。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>備註  
 priority_queue 必須為非空白，才能套用成員函式。 Priority_queue 頂端一律佔用的最大的項目容器中。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   priority_queue <int>::size_type i, iii;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
  
   q1.pop( );  
  
   iii = q1.size( );  
   cout << "After a pop, the priority_queue length is "   
        << iii << "." << endl;  
  
   const int& iv = q1.top( );  
   cout << "After a pop, the element at the top of the "  
        << "priority_queue is " << iv << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
After a pop, the priority_queue length is 2.  
After a pop, the element at the top of the priority_queue is 20.  
```  
  
##  <a name="a-namepriorityqueuepriorityqueuea-priorityqueuepriorityqueue"></a><a name="priority_queue__priority_queue"></a>  priority_queue:: priority_queue  
 建構 priority_queue 是空的或範圍，或另一個 priority_queue 的基底的容器物件的複本。  
  
```  
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```  
  
### <a name="parameters"></a>參數  
 *_ comp*  
 類型的比較函式 **constTraits** 用來排序 priority_queue，其預設值為比較函式的基底的容器中的項目。  
  
 `_Cont`  
 為其複本建構的 priority_queue 的基底的容器。  
  
 ` right`  
 Priority_queue 當中建構的集合的副本。  
  
 ` first`  
 要複製的元素範圍中第一個元素的位置。  
  
 ` last`  
 超出要複製之元素範圍的第一個元素的位置。  
  
### <a name="remarks"></a>備註  
 每個前三個建構函式指定空的初始 priority_queue，第二個指定的比較函式類型 ( ` comp`) 要用來建立項目和第三個明確指定的順序 `container_type` ( `_Cont`) 使用。 關鍵字 **明確** 隱藏某些類型的自動類型轉換。  
  
 第四個建構函式會指定一份 priority_queue ` right`。  
  
 最後三個建構函式會將範圍複製 [ * first、 last*) 的某個容器，並使用值來初始化逐漸 explicitness 中指定的比較函式類別的型別 priority_queue **特性** 和 `container_type`。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_ctor.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <deque>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function declares priority_queue  
   // with a default vector base container  
   priority_queue <int> q1;  
   cout << "q1 = ( ";  
   while ( !q1.empty( ) )  
   {  
      cout << q1.top( ) << " ";  
      q1.pop( );  
   }  
   cout << ")" << endl;  
  
   // Explicitly declares a priority_queue with nondefault  
   // deque base container  
   priority_queue <int, deque <int> > q2;  
   q2.push( 5 );  
   q2.push( 15 );  
   q2.push( 10 );  
   cout << "q2 = ( ";  
   while ( !q2.empty( ) )  
   {  
      cout << q2.top( ) << " ";  
      q2.pop( );  
   }  
   cout << ")" << endl;  
  
   // This method of printing out the elements of a priority_queue  
   // removes the elements from the priority queue, leaving it empty  
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;  
  
   // The third member function declares a priority_queue   
   // with a vector base container and specifies that the comparison   
   // function greater is to be used for ordering elements  
   priority_queue <int, vector<int>, greater<int> > q3;  
   q3.push( 2 );  
   q3.push( 1 );  
   q3.push( 3 );  
   cout << "q3 = ( ";  
   while ( !q3.empty( ) )  
   {  
      cout << q3.top( ) << " ";  
      q3.pop( );  
   }  
   cout << ")" << endl;  
  
   // The fourth member function declares a priority_queue and  
   // initializes it with elements copied from another container:  
   // first, inserting elements into q1, then copying q1 elements into q4  
   q1.push( 100 );  
   q1.push( 200 );  
   priority_queue <int> q4( q1 );  
   cout << "q4 = ( ";     
   while ( !q4.empty( ) )  
   {  
      cout << q4.top( ) << " ";  
      q4.pop( );  
   }  
   cout << ")" << endl;  
  
   // Creates an auxiliary vector object v5 to be used to initialize q5  
   vector <int> v5;  
   vector <int>::iterator v5_Iter;  
   v5.push_back( 10 );  
   v5.push_back( 30 );  
   v5.push_back( 20 );  
   cout << "v5 = ( " ;  
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )  
      cout << *v5_Iter << " ";  
   cout << ")" << endl;  
  
   // The fifth member function declares and  
   // initializes a priority_queue q5 by copying the  
   // range v5[ first,  last) from vector v5  
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q5 = ( ";  
   while ( !q5.empty( ) )  
   {  
      cout << q5.top( ) << " ";  
      q5.pop( );  
   }  
   cout << ")" << endl;  
  
   // The sixth member function declares a priority_queue q6  
   // with a comparison function greater and initializes q6  
   // by copying the range v5[ first,  last) from vector v5  
   priority_queue <int, vector<int>, greater<int> >   
      q6( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q6 = ( ";  
   while ( !q6.empty( ) )  
   {  
      cout << q6.top( ) << " ";  
      q6.pop( );  
   }  
   cout << ")" << endl;  
}  
```  
  
##  <a name="a-namepriorityqueuepusha-priorityqueuepush"></a><a name="priority_queue__push"></a>  priority_queue:: push  
 將元素加入至根據優先順序的運算子中的項目優先權佇列 <。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>參數  
 ` val`  
 加入至 priority_queue 頂端的項目。  
  
### <a name="remarks"></a>備註  
 Priority_queue 頂端是佔用最大的項目容器中的位置。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="a-namepriorityqueuesizea-priorityqueuesize"></a><a name="priority_queue__size"></a>  priority_queue:: size  
 Priority_queue 中傳回的項目數。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 Priority_queue 目前的長度。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, q2;  
   priority_queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The priority_queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 1.  
The priority_queue length is now 2.  
```  
  
##  <a name="a-namepriorityqueuesizetypea-priorityqueuesizetype"></a><a name="priority_queue__size_type"></a>  priority_queue:: size_type  
 不帶正負號的整數型別可以代表 priority_queue 中的項目數。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `size_type` 由 priority_queue 的基底容器。  
  
### <a name="example"></a>範例  
  請參閱範例 [大小](#priority_queue__size) 如需如何宣告和使用的範例 `size_type`。  
  
##  <a name="a-namepriorityqueuetopa-priorityqueuetop"></a><a name="priority_queue__top"></a>  priority_queue:: top  
 傳回 priority_queue 頂端最大項目的常數參考。  
  
```  
const_reference top() const;
```  
  
### <a name="return-value"></a>傳回值  
 最大項目，由參考 **特性** 函式、 priority_queue 的物件。  
  
### <a name="remarks"></a>備註  
 priority_queue 必須為非空白，才能套用成員函式。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_top.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="a-namepriorityqueuevaluetypea-priorityqueuevaluetype"></a><a name="priority_queue__value_type"></a>  priority_queue:: value_type  
 代表物件儲存為 priority_queue 中的項目類型的類型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `value_type` 由 priority_queue 的基底容器。  
  
### <a name="example"></a>範例  
  
```  
// pqueue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   priority_queue<int> q1;  
   q1.push( AnInt );  
   cout << "The element at the top of the priority_queue is "  
        << q1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the priority_queue is 69.  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

