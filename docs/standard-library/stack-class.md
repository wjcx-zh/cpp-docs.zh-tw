---
title: "stack 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::stack"
  - "std.stack"
  - "stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "堆疊，stack 類別"
  - "stack 類別"
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# stack 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範本容器配接器類別，其提供的功能限制將對項目的存取限制為最近加入一些基礎容器類型的項目。 Stack 類別用於務必要先釐清容器上只執行堆疊作業的情況。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type, class Container= deque <Type>>  
class stack  
```  
  
#### <a name="parameters"></a>參數  
 *Type*  
 要存放在堆疊中的項目資料類型。  
  
 `Container`  
 用來實作堆疊的基礎容器類型。 預設值是類別 `deque`*\< 類型>*。  
  
## <a name="remarks"></a>備註  
 類別的項目 **類型** 約定中第一個範本參數的堆疊物件是同義詞 [value_type](#stack__value_type) ，而且必須符合基礎容器類別中的項目類型 **容器** 約定由第二個範本參數。  **類型** 必須指派，如此就可以複製該類型的物件，並將值指派給該型別的變數。  
  
 堆疊的適當基礎容器類別包括 [deque](../standard-library/deque-class.md), ，[list 類別](../standard-library/list-class.md), ，和 [vector 類別](../standard-library/vector-class.md), ，或任何其他支援的作業序列容器 **回**, ，`push_back`, ，和 `pop_back`。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。  
  
 在堆疊的物件相等比較，才類別的項目 **類型** 是可以比較是否相等，而且小於-比可比較，才類別的項目 **類型** 小於-比可比較。  
  
-   Stack 類別支援後進先出 (LIFO) 的資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。  
  
-    [Queue 類別](../standard-library/queue-class.md) 支援先進先出 (FIFO) 資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制以這種方式只存取前端和後端項目是使用 queue 類別的原因。  
  
-    [Priority_queue 類別](../standard-library/priority-queue-class.md) 排序其項目，如此大的項目永遠都會列在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[堆疊](#stack__stack)|建構空的，或是基底容器物件複本的 `stack`。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#stack__container_type)|提供基底容器以讓 `stack` 調整的類型。|  
|[size_type](#stack__size_type)|不帶正負號的整數類型，可以表示 `stack` 中的項目數。|  
|[value_type](#stack__value_type)|此類型代表儲存為 `stack` 項目的物件類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[空白](#stack__empty)|測試 `stack` 是否為空白。|  
|[快顯](#stack__pop)|從 `stack` 頂端移除項目。|  
|[推播](#stack__push)|將項目加入 `stack` 的頂端。|  
|[大小](#stack__size)|傳回 `stack` 中項目的數目。|  
|[頁首](#stack__top)|傳回 `stack` 頂端項目的參考。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 堆疊>  
  
 **命名空間：** std  
  
##  <a name="a-namestackcontainertypea-stackcontainertype"></a><a name="stack__container_type"></a>  stack:: container_type  
 提供基底的容器必須採用型別。  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是樣板參數 `Container` 的同義字。 所有三個 STL 序列容器類別 — 向量類別、 清單類別，以及預設類別 deque — 符合需求，才能做堆疊物件的基底的容器。 也可能使用滿足這些需求的使用者定義型別。  
  
 如需有關 `Container`, ，請參閱 \< 備註 > 一節 [stack 類別](../standard-library/stack-class.md) 主題。  
  
### <a name="example"></a>範例  
  請參閱範例 [stack:: stack](#stack__stack) 如需如何宣告和使用的範例 `container_type`。  
  
##  <a name="a-namestackemptya-stackempty"></a><a name="stack__empty"></a>  stack:: empty  
 測試是否是空的堆疊。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 **true** 堆疊是空的; 如果 **false** 如果不是空的堆疊。  
  
### <a name="example"></a>範例  
  
```  
// stack_empty.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack <int> s1, s2;  
  
   s1.push( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The stack s1 is empty." << endl;  
   else  
      cout << "The stack s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The stack s2 is empty." << endl;  
   else  
      cout << "The stack s2 is not empty." << endl;  
}  
```  
  
```Output  
The stack s1 is not empty.  
The stack s2 is empty.  
```  
  
##  <a name="a-namestackpopa-stackpop"></a><a name="stack__pop"></a>  stack:: pop  
 從堆疊頂端的項目。  
  
```  
void pop();
```  
  
### <a name="remarks"></a>備註  
 堆疊必須是空的成員函式會套用。 堆疊的頂端是最近新增的項目佔據的位置，也是最後一個元素的容器結尾。  
  
### <a name="example"></a>範例  
  
```  
// stack_pop.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
  
   s1.pop( );  
  
   i = s1.size( );  
   cout << "After a pop, the stack length is "   
        << i << "." << endl;  
  
   i = s1.top( );  
   cout << "After a pop, the element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
After a pop, the stack length is 2.  
After a pop, the element at the top of the stack is 20.  
```  
  
##  <a name="a-namestackpusha-stackpush"></a><a name="stack__push"></a>  stack:: push  
 將項目加入至堆疊的頂端。  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>參數  
 ` val`  
 項目加入至堆疊的頂端。  
  
### <a name="remarks"></a>備註  
 堆疊的頂端是最近新增的項目佔據的位置，也是最後一個元素的容器結尾。  
  
### <a name="example"></a>範例  
  
```  
// stack_push.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
```  
  
##  <a name="a-namestacksizea-stacksize"></a><a name="stack__size"></a>  stack:: size  
 堆疊中傳回的項目數。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 堆疊的目前長度。  
  
### <a name="example"></a>範例  
  
```  
// stack_size.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
   stack <int>::size_type i;  
  
   s1.push( 1 );  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   s1.push( 2 );  
   i = s1.size( );  
   cout << "The stack length is now " << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 1.  
The stack length is now 2.  
```  
  
##  <a name="a-namestacksizetypea-stacksizetype"></a><a name="stack__size_type"></a>  stack:: size_type  
 不帶正負號的整數型別可以代表堆疊中的項目數。  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `size_type` 調整堆疊基底容器。  
  
### <a name="example"></a>範例  
  請參閱範例 [大小](#stack__size) 如需如何宣告和使用的範例 `size_type`。  
  
##  <a name="a-namestackstacka-stackstack"></a><a name="stack__stack"></a>  stack:: stack  
 建構的堆疊是空的或是屬於容器的基底類別的複本。  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 為其複本建構的堆疊的容器。  
  
### <a name="example"></a>範例  
  
```  
// stack_stack.cpp  
// compile with: /EHsc  
#include <stack>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares stack with default deque base container  
   stack <char> dsc1;  
  
   //Explicitly declares a stack with deque base container  
   stack <char, deque<char> > dsc2;  
  
   // Declares a stack with vector base containers  
   stack <int, vector<int> > vsi1;  
  
   // Declares a stack with list base container  
   stack <int, list<int> > lsi;  
  
   // The second member function copies elements from a container  
   vector<int> v1;  
   v1.push_back( 1 );  
   stack <int, vector<int> > vsi2( v1 );  
   cout << "The element at the top of stack vsi2 is "  
        << vsi2.top( ) << "." << endl;  
}  
```  
  
```Output  
The element at the top of stack vsi2 is 1.  
```  
  
##  <a name="a-namestacktopa-stacktop"></a><a name="stack__top"></a>  stack:: top  
 傳回在堆疊頂端的項目參考。  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>傳回值  
 在堆疊頂端的容器中的最後一個項目參考。  
  
### <a name="remarks"></a>備註  
 堆疊必須是空的成員函式會套用。 堆疊的頂端是最近新增的項目佔據的位置，也是最後一個元素的容器結尾。  
  
 如果傳回值 **頂端** 指派給 `const_reference`, ，不能修改堆疊物件。 如果傳回值 **頂端** 指派給 **參考**, ，可以修改堆疊物件。  
  
### <a name="example"></a>範例  
  
```  
// stack_top.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 1 );  
   s1.push( 2 );  
  
   int& i = s1.top( );  
   const int& ii = s1.top( );  
  
   cout << "The top integer of the stack s1 is "  
        << i << "." << endl;  
   i--;  
   cout << "The next integer down is "<< ii << "." << endl;  
}  
```  
  
```Output  
The top integer of the stack s1 is 2.  
The next integer down is 1.  
```  
  
##  <a name="a-namestackvaluetypea-stackvaluetype"></a><a name="stack__value_type"></a>  stack:: value_type  
 代表堆疊中的項目儲存的物件類型的類型。  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字 `value_type` 調整堆疊基底容器。  
  
### <a name="example"></a>範例  
  
```  
// stack_value_type.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   stack<int> s1;  
   s1.push( AnInt );  
   cout << "The element at the top of the stack is "  
        << s1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the stack is 69.  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

