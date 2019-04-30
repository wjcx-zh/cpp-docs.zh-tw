---
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: ed5e190f0c64aca3876d1cd1f05c9d75224355cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384760"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)

此範本類別描述控制不同長度排序的項目序列的有限存取的物件。 您使用的容器配接器`priority_queue`管理作為優先順序佇列基礎容器。

下列描述中`GValue`等同*值*後者是 ref 型別，除非在此情況下是`Value^`。 同樣地，`GContainer`等同*容器*後者是 ref 型別，除非在此情況下是`Container^`。

## <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>參數

*值*<br/>
受控制序列中項目的類型。

*Container*<br/>
基礎容器的類型。

## <a name="requirements"></a>需求

**標頭：** \<cliext/佇列 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[priority_queue::container_type (STL/CLR)](#container_type)|基礎容器的類型。|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|容器配接器的泛型介面型別。|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|容器配接器的泛型介面的項目型別。|
|[priority_queue::reference (STL/CLR)](#reference)|項目的參考類型。|
|[priority_queue::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|兩個項目的排序委派。|
|[priority_queue::value_type (STL/CLR)](#value_type)|元素的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|取代所有項目。|
|[priority_queue::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[priority_queue::get_container (STL/CLR)](#get_container)|存取基礎容器。|
|[priority_queue::pop (STL/CLR)](#pop)|移除 hghest 優先順序項目。|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|建構容器物件。|
|[priority_queue::push (STL/CLR)](#push)|加入新項目。|
|[priority_queue::size (STL/CLR)](#size)|計算元素的數目。|
|[priority_queue::top (STL/CLR)](#top)|存取最高優先順序項目。|
|[priority_queue::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|複製針對兩個元素的順序委派。|

|屬性|描述|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|存取最高優先順序項目。|

|運算子|描述|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|取代受控制的序列。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|重複的物件。|
|IPriorityQueue\<值、 容器 >|維護泛型容器配接器。|

## <a name="remarks"></a>備註

物件，配置並釋放它透過基礎的容器，型別所控制之序列的儲存體`Container`，儲存`Value`項目並視需要成長。 它會保留為堆積，與最高優先順序項目 （最上層項目） 隨時可供存取和卸除式排序序列。 物件會限制存取推送新的項目和拉出只是最高優先順序項目，實作優先順序佇列。

物件會排列它所控制藉由呼叫預存的委派物件的型別序列[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)。 當您建構 priority_queue; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(value_type, value_type)`。 您可以存取這個預存的物件藉由呼叫成員函式[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`。

這類委派物件必須強制執行嚴格弱式排序類型的值[priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:

`value_comp()(X, Y)` 傳回的結果相同的布林值，在每次呼叫。

如果`value_comp()(X, Y)`為 true，然後`value_comp()(Y, X)`必須為偽。

如果`value_comp()(X, Y)`為 true，然後`X`稱為排序之前`Y`。

如果`!value_comp()(X, Y) && !value_comp()(Y, X)`為 true，然後`X`和`Y`被視為具有對等順序。

對於任何項目`X`前面`Y`在受控制的序列，`key_comp()(Y, X)`為 false。 （預設委派物件的索引鍵永遠不會減少值中。）

最高優先順序項目，因此是其中一個任何其他項目之前未經過排序的項目。

由於基礎的容器會保留為堆積排序的項目：

容器必須支援隨機存取迭代器。

具有對等排序的項目可能會推出不同的順序，比他們已推送。 （順序不穩定）。

因此，基礎容器的候選項目包含[deque (STL/CLR)](../dotnet/deque-stl-clr.md)並[向量 (STL/CLR)](../dotnet/vector-stl-clr.md)。

## <a name="members"></a>成員

## <a name="assign"></a> priority_queue::assign (STL/CLR)

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要插入的容器配接器。

### <a name="remarks"></a>備註

此成員函式會指派`right.get_container()`至基礎容器。 您可以使用它來變更佇列的整個內容。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="const_reference"></a> priority_queue::const_reference (STL/CLR)

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

此類型描述項目的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="container_type"></a> priority_queue:: container_type (STL/CLR)

基礎容器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Container`的同義字。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="difference_type"></a> priority_queue::difference_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能是負數的項目計數。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="empty"></a> priority_queue:: empty (STL/CLR)

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[priority_queue:: size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`。 您可以使用它來測試 priority_queue 是否空白。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="generic_container"></a> priority_queue::generic_container (STL/CLR)

容器的泛型介面型別。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器配接器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="generic_value"></a> priority_queue::generic_value (STL/CLR)

使用容器的泛型介面的項目型別。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

此類型所描述型別的物件`GValue`，描述與此範本的容器類別的泛型介面使用的預存的項目值。 (`GValue`可能`value_type`或是`value_type^`如果`value_type`是 ref 型別。)

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="get_container"></a> priority_queue::get_container (STL/CLR)

存取基礎容器。

### <a name="syntax"></a>語法

```cpp
container_type get_container();
```

### <a name="remarks"></a>備註

此成員函式會傳回基礎容器。 您可以使用它來略過由容器包裝函式所加諸的限制。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="op_as"></a> priority_queue::operator= (STL/CLR)

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要複製的容器配接器。

### <a name="remarks"></a>備註

成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代受控制的序列中的受控制序列的複本*右*。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="pop"></a> priority_queue:: pop (STL/CLR)

移除最高 proirity 項目。

### <a name="syntax"></a>語法

```cpp
void pop();
```

### <a name="remarks"></a>備註

此成員函式中移除受控制的序列必須為非空白的最高優先順序項目。 您可以使用它來縮短佇列後端的一個項目。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queue"></a> priority_queue:: priority_queue (STL/CLR)

建構容器配接器物件。

### <a name="syntax"></a>語法

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>參數

*cont*<br/>
要複製的容器。

*first*<br/>
若要插入的範圍的開頭。

*last*<br/>
若要插入的範圍的結尾。

*pred*<br/>
排序受控制序列的述詞。

*right*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

建構函式：

`priority_queue();`

建立空的包裝的容器，以預設的排序的述詞。 您可以使用它來指定空的初始受控制的序列，以預設的排序的述詞。

建構函式：

`priority_queue(priority_queue<Value, Container>% right);`

建立包裝的容器，是一份`right.get_container()`，以排序的述詞`right.value_comp()`。 您使用它來指定初始受控制的序列的佇列物件所控制之序列的複本*右*，具有相同排序的述詞。

建構函式：

`priority_queue(priority_queue<Value, Container>^ right);`

建立包裝的容器，是一份`right->get_container()`，以排序的述詞`right->value_comp()`。 您使用它來指定初始受控制的序列的佇列物件所控制的序列複本`*right`，具有相同排序的述詞。

建構函式：

`explicit priority_queue(value_compare^ pred);`

建立空的包裝的容器，以排序的述詞*pred*。 您可以使用它來指定空的初始受控制的序列，指定排序的述詞。

建構函式：

`priority_queue(value_compare^ pred, container_type cont);`

建立空的包裝的容器，以排序的述詞*pred*，然後推送的所有項目*cont*您使用它來指定初始受控制的序列，從現有的容器指定排序的述詞。

建構函式：

`template<typename InIt> priority_queue(InIt first, InIt last);`

使用預設排序的述詞，建立空的包裝的容器，然後推入序列 [`first`， `last`)。 您可以使用它來指定排序的述詞指定從指定的 eqeuence，初始受控制的序列。

建構函式：

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

建立空的包裝的容器，以排序的述詞*pred*，然後將推入序列 [`first`， `last`)。 您可以使用它來指定排序的述詞指定從指定的 seqeuence，初始受控制的序列。

建構函式：

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

建立空的包裝的容器，以排序的述詞*pred*，然後將推入的所有項目*cont*再加上順序 [`first`， `last`)。 您可以使用它來指定排序的述詞指定從現有的容器和指定的 seqeuence，初始受控制的序列。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="push"></a> priority_queue:: push (STL/CLR)

加入新項目。

### <a name="syntax"></a>語法

```cpp
void push(value_type val);
```

### <a name="remarks"></a>備註

此成員函式插入值的項目`val`成受控制的序列，並重新排序受控制的序列，以維護堆積專業領域。 您可以使用它來將另一個項目新增至佇列。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="reference"></a> priority_queue::reference (STL/CLR)

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述項目的參考。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="size"></a> priority_queue:: size (STL/CLR)

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列的項目數。 如果您在意順序是否有非零值的大小，請參閱[priority_queue:: empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="size_type"></a> priority_queue:: size_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述的非負數的項目計數。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="to_array"></a> priority_queue::to_array (STL/CLR)

將受控制的序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

此成員函式會傳回包含之受控制的序列的陣列。 您可以使用它來取得陣列形式中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
d c b a
c a b
```

## <a name="top"></a> priority_queue:: top (STL/CLR)

存取最高優先順序項目。

### <a name="syntax"></a>語法

```cpp
reference top();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制的序列必須為非空白的頂端 （最高優先順序） 項目參考。 您可以使用它來存取的最高優先順序項目中，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="top_item"></a> priority_queue::top_item (STL/CLR)

存取最高優先順序項目。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性存取受控制的序列必須為非空白的頂端 （最高優先順序） 項目。 您可以使用它來讀取或寫入的最高優先順序項目中，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="value_comp"></a> priority_queue::value_comp (STL/CLR)

複製針對兩個元素的順序委派。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

此成員函式會傳回用來排序受控制的序列的順序委派。 您可以使用它來比較兩個值。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="value_compare"></a> priority_queue::value_compare (STL/CLR)

兩個值的排序委派。

### <a name="syntax"></a>語法

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>備註

此類型為委派，來決定是否要將第一個引數排序之前，第二個的同義字。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="value_type"></a> priority_queue:: value_type (STL/CLR)

元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

類型是範本參數的同義字*值*。

### <a name="example"></a>範例

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```