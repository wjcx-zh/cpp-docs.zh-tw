---
title: priority_queue 類別
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
ms.openlocfilehash: 8a1b33e45d066082a0f225067db84a6240e8fc53
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232946"
---
# <a name="priority_queue-class"></a>priority_queue 類別

範本容器配接器類別，它提供的限制功能可限制存取某些基礎容器類型的最上層項目，且這一律為最大或最高優先順序。 新項目可加入至 priority_queue，並且可以檢查或移除 priority_queue 的最上層項目。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>參數

*型*\
要存放在 priority_queue 中的項目資料類型。

*箱*\
用來實作 priority_queue 的基礎容器類型。

*何*\
此類型提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在 priority_queue 中的相對順序。 這個引數是選用引數，且預設值是二元述詞 `less<typename Container::value_type>`。

## <a name="remarks"></a>備註

`Type`在佇列物件的第一個樣板參數中，類別約定的元素與[value_type](#value_type)同義，而且必須符合第二個樣板參數所約定之基礎容器類別中的元素類型 `Container` 。 `Type`必須是可指派的，如此才能複製該類型的物件，並將值指派給該類型的變數。

Priority_queue 會藉由呼叫類別的預存函式物件，排序它所控制的序列 `Traits` 。 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。

適用於 priority_queue 的基礎容器類別包括 [deque 類別](../standard-library/deque-class.md)和預設的 [vector 類別](../standard-library/vector-class.md)，或是任何其他支援 `front`、`push_back` 和 `pop_back` 作業，以及隨機存取迭代器的序列容器。 基礎容器類別會封裝在容器介面卡內，它只會公開有限的序列容器成員函式集做為公用的介面。

將項目加入至 `priority_queue` 或從中移除項目，都具有對數複雜度。 存取 `priority_queue` 中的項目具有常數複雜度。

有三種由 C++ 標準程式庫定義的容器配接器類型：stack、queue 和 priority_queue。 每個類型都會限制某些基礎容器類別的功能，以精確地為標準資料結構提供受控制的介面。

- [Stack 類別](../standard-library/stack-class.md)支援後進先出（LIFO）的資料結構。 就好像盤子的堆疊一樣，這是一種較為貼切好記的類比。 項目 (盤子) 可能會插入、檢查，或只從堆疊頂端移除，這是基底容器尾端的最後一個項目。 限制只存取最上層項目是使用 stack 類別的原因。

- [Queue 類別](../standard-library/queue-class.md)支援先進先出（FIFO）的資料結構。 就好像人們排隊等候銀行櫃員一樣，這是一種較為貼切好記的類比。 項目 (人) 可能會加入隊伍的尾端，以及從隊伍的前面移除。 隊伍的前端和後端都可能會進行檢查。 限制以這種方式只存取前端和後端項目是使用 queue 類別的原因。

- priority_queue 類別會排序其項目，使最大的項目一律位在頂端位置。 它支援插入項目，以及檢查和移除頂端項目。 就好像依照年齡、身高或某些其他條件來排列一群人一樣，這是一種較為貼切好記的類比。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[priority_queue](#priority_queue)|建構 `priority_queue`，它可以是空的，或是基底容器物件範圍的複本，或是其他 `priority_queue` 的複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[container_type](#container_type)|提供基底容器以讓 `priority_queue` 調整的類型。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示 `priority_queue` 中的項目數。|
|[value_type](#value_type)|此類型代表儲存為 `priority_queue` 項目的物件類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[empty](#empty)|測試 `priority_queue` 是否為空白。|
|[提示](#pop)|從頂端位置移除 `priority_queue` 的最大項目。|
|[push](#push)|根據運算子 < 的項目優先順序，將項目加入到優先權佇列。|
|[size](#size)|傳回 `priority_queue` 中項目的數目。|
|[top](#top)|傳回 `priority_queue` 頂端最大項目的 const 參考。|

## <a name="requirements"></a>需求

**標頭：**\<queue>

**命名空間：** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a>priority_queue：： container_type

提供要配接之基底容器的類型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Container` 的同義字。 C++ 標準程式庫序列容器類別 `deque` 和預設類別 `vector` 都符合用來當作 priority_queue 物件之基底類別的需求。 也可以使用滿足該要求的使用者定義類型。

如需有關 `Container` 的詳細資訊，請參閱 [priority_queue 類別](../standard-library/priority-queue-class.md)主題的＜備註＞一節。

### <a name="example"></a>範例

如需如何宣告及使用 `container_type` 的範例，請參閱 [priority_queue](#priority_queue) 的範例。

## <a name="priority_queueempty"></a><a name="empty"></a>priority_queue：： empty

測試 priority_queue 是否是空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 priority_queue 是空的，則為，**`false`** 如果 priority_queue 不是空的。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuepop"></a><a name="pop"></a>priority_queue：:p op

從頂端位置移除 priority_queue 的最大項目。

```cpp
void pop();
```

### <a name="remarks"></a>備註

priority_queue 必須為非空白，才能套用成員函式。 priority_queue 的頂端一律由容器中最大的項目佔用。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a>priority_queue：:p riority_queue

建構 priority_queue，它可以是空的，或是基底容器物件範圍的複本，或是另一個 priority_queue 的複本。

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>參數

*_comp*\
類型為 **constTraits** 並用來排序 priority_queue 中項目的比較函式，預設為基底容器的比較函式。

*_Cont*\
建構的 priority_queue 將成為複本的基底容器。

*再*\
建構的集合將成為複本的 priority_queue。

*頭*\
要複製的元素範圍中第一個元素的位置。

*次*\
超出要複製之元素範圍的第一個元素的位置。

### <a name="remarks"></a>備註

前三個程式的每一個都指定空的初始 priority_queue，第二個則指定 `comp` 要用來建立元素順序的比較函數（）類型，以及第三個明確指定 `container_type` 要使用的（ `_Cont` ）。 關鍵字會 **`explicit`** 隱藏某些類型的自動類型轉換。

第四個函式會指定 priority_queue*許可權*的複本。

最後三個函式會複製 \[ 某些容器的*第一個*、*最後一個*範圍，並使用這些值來初始化 priority_queue，並在指定類別和的比較函數類型時增加越來越明確 `Traits` `container_type` 。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuepush"></a><a name="push"></a>priority_queue：:p ush

根據運算子 < 的項目優先順序，將項目加入到優先權佇列。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>參數

*初始值*\
加入到 priority_queue 頂端的項目。

### <a name="remarks"></a>備註

priority_queue 的頂端是由容器中最大的項目佔用的位置。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuesize"></a><a name="size"></a>priority_queue：： size

傳回 priority_queue 中的項目數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

priority_queue 的目前長度。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuesize_type"></a><a name="size_type"></a>priority_queue：： size_type

不帶正負號的整數類型，可以表示 priority_queue 中的項目數。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>備註

此類型和由 priority_queue 配接的基底容器 `size_type` 同義。

### <a name="example"></a>範例

如需如何宣告及使用 `size_type` 的範例，請參閱 [size](#size) 的範例。

## <a name="priority_queuetop"></a><a name="top"></a>priority_queue：： top

傳回 priority_queue 頂端最大項目的常數參考。

```cpp
const_reference top() const;
```

### <a name="return-value"></a>傳回值

最大元素的參考，由函式所決定 `Traits` ，priority_queue 的物件。

### <a name="remarks"></a>備註

priority_queue 必須為非空白，才能套用成員函式。

### <a name="example"></a>範例

```cpp
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

## <a name="priority_queuevalue_type"></a><a name="value_type"></a>priority_queue：： value_type

此類型代表儲存為 priority_queue 項目的物件類型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>備註

此類型和由 priority_queue 配接的基底容器 `value_type` 同義。

### <a name="example"></a>範例

```cpp
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

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
