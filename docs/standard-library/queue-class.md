---
title: "queue 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.queue"
  - "std::queue"
  - "queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queue 類別"
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# queue 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範本容器配接器類別，提供一些基本的容器類型，限制的存取權的正面和背面的項目功能的限制。 可以在後端加入或移除最上層，項目，並且可以檢查項目，在任一端的佇列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type, class Container = deque <Type>>  
class queue  
```  
  
#### <a name="parameters"></a>參數  
 *Type*  
 要儲存在佇列的項目資料類型  
  
 `Container`  
 用來實作佇列基礎容器的類型。  
  
## <a name="remarks"></a>備註  
 類別的項目 **類型** 約定第一個範本中的佇列物件的參數是同義詞 [value_type](#queue__value_type) ，而且必須符合基礎容器類別中的項目類型 **容器** 約定由第二個範本參數。  **類型** 必須指派，如此就可以複製該類型的物件，並將值指派給該型別的變數。  
  
 適用的佇列的基礎容器類別包括 [deque](../standard-library/deque-class.md) 和 [清單](../standard-library/list-class.md), ，或任何其他支援的作業序列容器 `front`, ，**回**, ，`push_back`, ，和 `pop_front`。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。  
  
 佇列的物件相等比較，才類別的項目 **類型** 是相等的比較，，而且小於-比可比較，才類別的項目 **類型** 小於-比可比較。  
  
 有三種類型的 STL 所定義的容器配接器︰ 堆疊、 佇列和 priority_queue。 每個會限制一些基礎容器類別，以提供標準的資料結構的精確地控制的介面的功能。  
  
-    [Stack 類別](../standard-library/stack-class.md) 支援後進先出 (LIFO) 資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。  
  
-   Queue 類別支援的先進先出 (FIFO) 資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制存取只正面和背面元素以這種方式是使用佇列類別的原因。  
  
-    [Priority_queue 類別](../standard-library/priority-queue-class.md) 排序其項目，如此大的項目永遠都會列在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[佇列](#queue__queue)|建構空的，或是基底容器物件複本的 `queue`。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#queue__container_type)|類型，提供基底的容器必須採用由 `queue`。|  
|[size_type](#queue__size_type)|不帶正負號的整數類型，可以表示 `queue` 中的項目數。|  
|[value_type](#queue__value_type)|此類型代表儲存為 `queue` 項目的物件類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[上一步]](#queue__back)|傳回參考至最後一個和最近新增項目在支援的 `queue`。|  
|[空白](#queue__empty)|測試 `queue` 是否為空白。|  
|[前端](#queue__front)|傳回最前面的第一個元素的參考 `queue`。|  
|[快顯](#queue__pop)|從前端移除的項目 `queue`。|  
|[推播](#queue__push)|將元素加入至最後一 `queue`。|  
|[大小](#queue__size)|傳回 `queue` 中項目的數目。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 佇列>  
  
 **命名空間：** std  
  
##  <a name="a-namequeuebacka-queueback"></a><a name="queue__back"></a>  queue:: back  
 傳回參考的最後一個和最近新增項目佇列的背面。  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>傳回值  
 佇列的最後一個項目。 如果佇列是空的則傳回值會是未定義。  
  
### <a name="remarks"></a>備註  
 如果傳回值 **回** 指派給 `const_reference`, ，不能修改佇列物件。 如果傳回值 **回** 指派給 **參考**, ，可以修改佇列物件。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空的佇列中的項目，將會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// queue_back.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 11 );  
  
   int& i = q1.back( );  
   const int& ii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << i   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << ii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuecontainertypea-queuecontainertype"></a><a name="queue__container_type"></a>  queue:: container_type  
 提供基底的容器必須採用型別。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是樣板參數 `Container` 的同義字。 兩個 STL 序列容器類別 — 清單類別，而且預設 deque 類別 — 符合需求，才能做為佇列物件的基底的容器。 也可能使用滿足需求的使用者定義型別。  
  
 如需有關 `Container`, ，請參閱 \< 備註 > 一節 [queue 類別](../standard-library/queue-class.md) 主題。  
  
### <a name="example"></a>範例  
  請參閱範例 [佇列](#queue__queue) 如需如何宣告和使用的範例 `container_type`。  
  
##  <a name="a-namequeueemptya-queueempty"></a><a name="queue__empty"></a>  queue:: empty  
 如果佇列是空的測試。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 **true** 佇列是空的; 如果 **false** 如果不是空的佇列。  
  
### <a name="example"></a>範例  
  
```  
// queue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue <int> q1, q2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The queue q1 is empty." << endl;  
   else  
      cout << "The queue q1 is not empty." << endl;  
  
   if ( q2.empty( ) )  
      cout << "The queue q2 is empty." << endl;  
   else  
      cout << "The queue q2 is not empty." << endl;  
}  
```  
  
```Output  
The queue q1 is not empty.  
The queue q2 is empty.  
```  
  
##  <a name="a-namequeuefronta-queuefront"></a><a name="queue__front"></a>  queue:: front  
 傳回在佇列前面的第一個元素的參考。  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>傳回值  
 佇列的第一個項目。 如果佇列是空的則傳回值會是未定義。  
  
### <a name="remarks"></a>備註  
 如果傳回值 `front` 指派給 `const_reference`, ，不能修改佇列物件。 如果傳回值 `front` 指派給 **參考**, ，可以修改佇列物件。  
  
 成員函式傳回 **參考** 受控制序列的第一個元素，必須是空白。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取空的佇列中的項目，將會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  
```  
// queue_front.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   int& ii = q1.back( );  
   int& iii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << ii   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << iii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuepopa-queuepop"></a><a name="queue__pop"></a>  queue:: pop  
 從佇列前端移除元素。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>備註  
 佇列必須是空的成員函式會套用。 佇列頂端是最近新增的項目佔據的位置，也是最後一個元素的容器結尾。  
  
### <a name="example"></a>範例  
  
```  
// queue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
  
   q1.pop( );  
  
   i = q1.size( );  
   cout << "After a pop the queue length is "   
        << i << "." << endl;  
  
   i = q1. front ( );  
   cout << "After a pop, the element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
After a pop the queue length is 2.  
After a pop, the element at the front of the queue is 20.  
```  
  
##  <a name="a-namequeuepusha-queuepush"></a><a name="queue__push"></a>  queue:: push  
 將元素加入至佇列的最下層。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>參數  
 `val`  
 加入至佇列的最下層的項目。  
  
### <a name="remarks"></a>備註  
 佇列的上一步是最近新增的項目佔據的位置，結尾的容器的最後一個元素。  
  
### <a name="example"></a>範例  
  
```  
// queue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
```  
  
##  <a name="a-namequeuequeuea-queuequeue"></a><a name="queue__queue"></a>  queue:: queue  
 建構的佇列是空的或是屬於基底的容器物件的複本。  
  
```  
queue();

explicit queue(const container_type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
  **Const** 建構的佇列是有要複製的容器。  
  
### <a name="remarks"></a>備註  
 佇列的預設基底容器是 deque。 您也可以指定清單做為基底的容器，但您無法指定向量，因為它缺少必要 `pop_front` 成員函式。  
  
### <a name="example"></a>範例  
  
```  
// queue_queue.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queue with default deque base container  
   queue <char> q1;  
  
   // Explicitly declares a queue with deque base container  
   queue <char, deque<char> > q2;  
  
   // These lines don't cause an error, even though they  
   // declares a queue with a vector base container  
   queue <int, vector<int> > q3;  
   q3.push( 10 );  
   // but the following would cause an error because vector has   
   // no pop_front member function  
   // q3.pop( );  
  
   // Declares a queue with list base container  
   queue <int, list<int> > q4;  
  
   // The second member function copies elements from a container  
   list<int> li1;  
   li1.push_back( 1 );  
   li1.push_back( 2 );  
   queue <int, list<int> > q5( li1 );  
   cout << "The element at the front of queue q5 is "  
        << q5.front( ) << "." << endl;  
   cout << "The element at the back of queue q5 is "  
        << q5.back( ) << "." << endl;  
}  
```  
  
```Output  
The element at the front of queue q5 is 1.  
The element at the back of queue q5 is 2.  
```  
  
##  <a name="a-namequeuesizea-queuesize"></a><a name="queue__size"></a>  queue:: size  
 傳回佇列中的項目數目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 目前的佇列長度。  
  
### <a name="example"></a>範例  
  
```  
// queue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2;  
   queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 1.  
The queue length is now 2.  
```  
  
##  <a name="a-namequeuesizetypea-queuesizetype"></a><a name="queue__size_type"></a>  queue:: size_type  
 不帶正負號的整數型別可以代表佇列中的項目數。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `size_type` 調整佇列的基底容器。  
  
### <a name="example"></a>範例  
  請參閱範例 [queue:: front](#queue__front) 如需如何宣告和使用的範例 `size_type`。  
  
##  <a name="a-namequeuevaluetypea-queuevaluetype"></a><a name="queue__value_type"></a>  queue:: value_type  
 表示在佇列中的項目儲存的物件類型的類型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `value_type` 調整佇列的基底容器。  
  
### <a name="example"></a>範例  
  
```  
// queue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   queue<int> q1;  
   q1.push(AnInt);  
   cout << "The element at the front of the queue is "  
        << q1.front( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the front of the queue is 69.  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

