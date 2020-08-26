---
title: queue 類別
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: e0bfa4ab037b52b237bd674d5f705de4e9699383
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832603"
---
# <a name="queue-class"></a>queue 類別

範本容器配接器類別，它針對某些基礎容器類型提供功能限制，限制存取前端和後端的項目。 您可以從後端加入項目，或是從前端移除項目，並且可以在佇列的任一端檢查項目。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>參數

*類型*\
要存放在佇列中的項目資料類型

*容器*\
用來實作佇列的基礎容器類型。

## <a name="remarks"></a>備註

`Type`在佇列物件的第一個樣板參數中，約定類別的元素與[value_type](#value_type)同義，且必須符合第二個樣板參數所約定之基礎容器類別中的元素類型 `Container` 。 必須是可指派的，如此一來，就可以 `Type` 複製該類型的物件，並將值指派給該類型的變數。

適用于佇列的適用基礎容器類別包括 [deque](../standard-library/deque-class.md) 和 [list](../standard-library/list-class.md)，或任何其他支援 `front` 、、和作業的時序容器 `back` `push_back` `pop_front` 。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。

只有當類別的專案 `Type` 是相等的可比較，且只有在類別的元素小於比較時才可比較，佇列物件才可進行相等比較 `Type` 。

有三種由 C++ 標準程式庫定義的容器配接器類型：stack、queue 和 priority_queue。 每個類型都會限制某些基礎容器類別的功能，以精確地為標準資料結構提供受控制的介面。

- [Stack 類別](../standard-library/stack-class.md)支援後進先出 (LIFO) 資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。

- queue 類別支援先進先出 (FIFO) 的資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制以這種方式只存取前端和後端項目是使用 queue 類別的原因。

- [priority_queue 類別](../standard-library/priority-queue-class.md)會排序其項目，使最大的項目一律位在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[佇列](#queue)|建構空的，或是基底容器物件複本的 `queue`。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[container_type](#container_type)|提供基底容器以讓 `queue` 配接的類型。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `queue` 中的項目數。|
|[value_type](#value_type)|此類型代表儲存為 `queue` 項目的物件類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[返回](#back)|傳回 `queue` 後端最後且最近新增的項目。|
|[empty](#empty)|測試 `queue` 是否為空白。|
|[前面](#front)|傳回 `queue` 前端第一個項目的參考。|
|[流行](#pop)|從 `queue` 前端移除項目。|
|[push](#push)|將項目加入 `queue` 的後端。|
|[size](#size)|傳回 `queue` 中項目的數目。|

## <a name="back"></a><a name="back"></a> 返回

傳回佇列後端最後且最近新增的項目。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>傳回值

佇列的最後一個項目。 如果佇列是空的，傳回值為未定義。

### <a name="remarks"></a>備註

如果 `back` 的傳回值已指派給 `const_reference`，則無法修改佇列物件。 如果的傳回值 `back` 已指派給 `reference` ，則可以修改佇列物件。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空佇列中的項目，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
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

## <a name="container_type"></a><a name="container_type"></a> container_type

提供要配接之基底容器的類型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Container` 的同義字。 有兩種 C++ 標準程式庫序列容器類別：list 類別和預設 deque 類別，都符合用來當作佇列物件之基底類別的需求。 也可以使用滿足該要求的使用者定義類型。

如需有關 `Container` 的詳細資訊，請參閱 [queue 類別](../standard-library/queue-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 `container_type` 的範例，請參閱 [queue](#queue) 的範例。

## <a name="empty"></a><a name="empty"></a> 空

測試佇列是否為空白。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果佇列是空的，則為。 **`false`** 如果佇列不是空的。

### <a name="example"></a>範例

```cpp
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

## <a name="front"></a><a name="front"></a> 前面

傳回佇列前端第一個項目的參考。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>傳回值

佇列的第一個項目。 如果佇列是空的，傳回值為未定義。

### <a name="remarks"></a>備註

如果 `front` 的傳回值已指派給 `const_reference`，則無法修改佇列物件。 如果的傳回值 `front` 已指派給 `reference` ，則可以修改佇列物件。

成員函式會將 `reference` 設為受控制序列的第一個專案，而該專案必須是空的。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空佇列中的項目，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
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

## <a name="pop"></a><a name="pop"></a> 流行

從佇列前端移除項目。

```cpp
void pop();
```

### <a name="remarks"></a>備註

佇列必須為非空白，才能套用成員函式。 佇列頂端是最近新增之項目所佔用的位置，也是位於容器結尾的最後一個項目。

### <a name="example"></a>範例

```cpp
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

## <a name="push"></a><a name="push"></a> 推

將項目加入佇列的後端。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
加入至佇列後端的項目。

### <a name="remarks"></a>備註

佇列後端是最近新增之項目所佔用的位置，也是位於容器結尾的最後一個項目。

### <a name="example"></a>範例

```cpp
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

## <a name="queue"></a><a name="queue"></a> 佇列

建構佇列，它可以是空的，或是基底容器物件的複本。

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>參數

*對*\
**`const`** 結構化佇列要作為複本的容器。

### <a name="remarks"></a>備註

佇列的預設基底容器是 deque。 您也可以指定 list 做為基底容器，但您不能指定 vector，因為它缺少必要的 `pop_front` 成員函式。

### <a name="example"></a>範例

```cpp
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

## <a name="size"></a><a name="size"></a> 大小

傳回佇列中的項目數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

佇列目前的長度。

### <a name="example"></a>範例

```cpp
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

## <a name="size_type"></a><a name="size_type"></a> size_type

不帶正負號的整數類型，可以表示佇列中的項目數。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>備註

此類型和由佇列配接的基底容器 `size_type` 同義。

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [queue::front](#front) 的範例。

## <a name="value_type"></a><a name="value_type"></a> value_type

此類型代表儲存為佇列項目的物件類型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>備註

此類型和由佇列配接的基底容器 `value_type` 同義。

### <a name="example"></a>範例

```cpp
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

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
