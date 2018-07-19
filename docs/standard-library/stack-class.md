---
title: stack 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
dev_langs:
- C++
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b933029f7180292e1c9e392bf2ab09e8dbcb204
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963221"
---
# <a name="stack-class"></a>stack 類別

範本容器配接器類別，其提供的功能限制將對項目的存取限制為最近加入一些基礎容器類型的項目。 Stack 類別用於務必要先釐清容器上只執行堆疊作業的情況。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>參數

*型別*来儲存在堆疊中的項目資料類型。

*容器*用來實作堆疊的基礎容器類型。 預設值是 `deque`*\<Type>* 類別。

## <a name="remarks"></a>備註

類別的元素`Type`中的第一個範本約定堆疊物件的參數是同義詞[value_type](#value_type) ，而且必須符合的基礎容器類別中的項目類型`Container`所規定第二個樣板參數。 `Type`必須是可指派，，如此就可以複製該類型的物件，並將值指派給該類型的變數。

適當的堆疊的基礎容器類別包括[deque](../standard-library/deque-class.md)， [list 類別](../standard-library/list-class.md)，並[vector 類別](../standard-library/vector-class.md)，或任何其他支援的作業序列容器`back`， `push_back`，和`pop_back`。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。

堆疊物件是否相等比較，並且只有當類別的元素`Type`進行等號比較，小於-比比較，並且只有當類別的項目`Type`小於-比較。

- Stack 類別支援後進先出 (LIFO) 的資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。

- [queue 類別](../standard-library/queue-class.md)支援先進先出 (FIFO) 的資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制以這種方式只存取前端和後端項目是使用 queue 類別的原因。

- [priority_queue 類別](../standard-library/priority-queue-class.md)會排序其項目，使最大的項目一律位在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[stack](#stack)|建構空的，或是基底容器物件複本的 `stack`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[container_type](#container_type)|提供基底容器以讓 `stack` 調整的類型。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `stack` 中的項目數。|
|[value_type](#value_type)|此類型代表儲存為 `stack` 項目的物件類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[empty](#empty)|測試 `stack` 是否為空白。|
|[pop](#pop)|從 `stack` 頂端移除項目。|
|[push](#push)|將項目加入 `stack` 的頂端。|
|[size](#size)|傳回 `stack` 中項目的數目。|
|[top](#top)|傳回 `stack` 頂端項目的參考。|

## <a name="requirements"></a>需求

**標頭︰**\<stack>

**命名空間：** std

## <a name="container_type"></a>  stack::container_type

提供要配接之基底容器的類型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Container`的同義字。 這三種 C++ 標準程式庫序列容器類別 (vector 類別、list 類別和預設 deque 類別) 都符合用來做為堆疊物件之基底容器的需求。 您也可以使用滿足該要求的使用者定義類型。

如需 `Container` 的詳細資訊，請參閱 [stack 類別](../standard-library/stack-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 `container_type` 的範例，請參閱 [stack::stack](#stack) 的範例。

## <a name="empty"></a>  stack::empty

測試堆疊是否為空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果堆疊是空的，即為 **true**；如果堆疊不是空的，則為 **false**。

### <a name="example"></a>範例

```cpp
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

## <a name="pop"></a>  stack::pop

從堆疊頂端移除項目。

```cpp
void pop();
```

### <a name="remarks"></a>備註

堆疊不得為空，才能套用成員函式。 堆疊頂端是最近新增項目所佔用的位置，也是位於容器結尾的最後一個項目。

### <a name="example"></a>範例

```cpp
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

## <a name="push"></a>  stack::push

將項目加入至堆疊的最上方結尾。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>參數

*val*將元素加入至堆疊的頂端。

### <a name="remarks"></a>備註

堆疊頂端是最近新增項目所佔用的位置，也是位於容器結尾的最後一個項目。

### <a name="example"></a>範例

```cpp
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

## <a name="size"></a>  stack::size

傳回堆疊中的項目數。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

堆疊目前的長度。

### <a name="example"></a>範例

```cpp
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

## <a name="size_type"></a>  stack::size_type

不帶正負號的整數類型，可以表示堆疊中的項目數。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>備註

此類型與由堆疊所配接的基底容器 `size_type` 同義。

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例。

## <a name="stack"></a>  stack::stack

建構空的堆疊，或是基底容器類別複本的堆疊。

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>參數

*右*要從中複製所建構的堆疊的容器。

### <a name="example"></a>範例

```cpp
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

## <a name="top"></a>  stack::top

傳回堆疊頂端項目的參考。

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>傳回值

堆疊頂端之容器中最後一個項目的參考。

### <a name="remarks"></a>備註

堆疊不得為空，才能套用成員函式。 堆疊頂端是最近新增項目所佔用的位置，也是位於容器結尾的最後一個項目。

如果傳回值`top`指派給`const_reference`，無法修改堆疊物件。 如果傳回值`top`指派給`reference`，可以修改堆疊物件。

### <a name="example"></a>範例

```cpp
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

## <a name="value_type"></a>  stack::value_type

一個類型，代表堆疊中儲存為項目的物件類型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>備註

此類型與由堆疊所配接的基底容器 `value_type` 同義。

### <a name="example"></a>範例

```cpp
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

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
