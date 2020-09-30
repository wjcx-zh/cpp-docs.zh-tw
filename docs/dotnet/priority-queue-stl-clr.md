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
ms.openlocfilehash: fd87c39db279fb70d5c5b5f20e583251dc519755
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502395"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

此樣板類別描述一個物件，該物件可控制具有有限存取權之元素的不同長度排序次序。 您可以使用容器介面卡 `priority_queue` ，以優先順序佇列的形式管理基礎容器。

在下列描述中，與 `GValue` *值* 相同，除非後者是 ref 型別，在這種情況下就是 `Value^` 。 同樣地，與 `GContainer` *容器* 相同，除非後者是 ref 類型，在此情況下為 `Container^` 。

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

*容器*<br/>
基礎容器的類型。

## <a name="requirements"></a>需求

**標頭：**\<cliext/queue>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[priority_queue::container_type (STL/CLR)](#container_type)|基礎容器的類型。|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|容器介面卡的泛型介面型別。|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|容器介面卡泛型介面的元素類型。|
|[priority_queue::reference (STL/CLR)](#reference)|項目的參考類型。|
|[priority_queue::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|兩個元素的順序委派。|
|[priority_queue::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|取代所有項目。|
|[priority_queue::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[priority_queue::get_container (STL/CLR)](#get_container)|存取基礎容器。|
|[priority_queue::pop (STL/CLR)](#pop)|移除 hghest-priority 元素。|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|建構容器物件。|
|[priority_queue::push (STL/CLR)](#push)|新增元素。|
|[priority_queue::size (STL/CLR)](#size)|計算元素的數目。|
|[priority_queue::top (STL/CLR)](#top)|存取最高優先順序的元素。|
|[priority_queue::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|複製兩個項目的排序委派。|

|屬性|描述|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|存取最高優先順序的元素。|

|運算子|描述|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|取代受控制的序列。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|IPriorityQueue\<Value, Container>|維護一般容器介面卡。|

## <a name="remarks"></a>備註

物件會根據類型的基礎容器來配置和釋出其所控制之序列的儲存體，以 `Container` 儲存專案 `Value` 並依需求成長。 它會將順序保持為堆積，而最高優先順序元素 (最上層元素，) 可以立即存取和移除。 物件會限制存取推送新的元素，並只會快顯最高優先順序的專案，以執行優先順序佇列。

物件會藉由呼叫 priority_queue：： value_compare 類型的預存委派物件，來排序它所控制的序列 [ (STL/CLR) ](#value_compare)。 當您建立 priority_queue 時，可以指定預存的委派物件。如果您未指定委派物件，預設值就是比較 `operator<(value_type, value_type)` 。 您可以藉由呼叫成員函式[priority_queue：： value_comp (STL/CLR) ](#value_comp)來存取這個儲存的物件 `()` 。

這類委派物件必須在類型 priority_queue：： value_type 的值上強制執行嚴格弱式排序， [ (STL/CLR) ](#value_type)。 這表示，針對任何兩個金鑰， `X` 以及 `Y` ：

`value_comp()(X, Y)` 每次呼叫時，都會傳回相同的布林值結果。

如果 `value_comp()(X, Y)` 是 true，則 `value_comp()(Y, X)` 必須為 false。

如果 `value_comp()(X, Y)` 是 true，則 `X` 會被視為之前的排序 `Y` 。

如果 `!value_comp()(X, Y) && !value_comp()(Y, X)` 是 true，則 `X` 和 `Y` 也稱為具有對等的排序。

若為 `X` `Y` 受控制序列中的任何元素， `key_comp()(Y, X)` 則為 false。  (預設的委派物件，索引鍵的值永遠不會減少。 ) 

最高優先順序的元素就是其中一個未在任何其他專案之前排序的元素。

因為基礎容器會將元素保留為堆積：

容器必須支援隨機存取反覆運算器。

具有對等順序的元素，可能會以不同于推送的順序來進行快顯。  (排序不穩定。 ) 

因此，基礎容器的候選項目包括 [deque (stl/clr) ](../dotnet/deque-stl-clr.md) 和 [vector (stl/clr) ](../dotnet/vector-stl-clr.md)。

## <a name="members"></a>成員

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a> priority_queue：： assign (STL/CLR) 

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要插入的容器介面卡。

### <a name="remarks"></a>備註

成員函式會指派 `right.get_container()` 給基礎容器。 您可以使用它來變更佇列的整個內容。

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

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a> priority_queue：： const_reference (STL/CLR) 

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

型別描述元素的常數參考。

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

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a> priority_queue：： container_type (STL/CLR) 

基礎容器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Container` 的同義字。

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

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a> priority_queue：:d ifference_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能的負元素計數。

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

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a> priority_queue：： empty (STL/CLR) 

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[priority_queue：： size (STL/CLR) ](#size) `() == 0` 。 您可以使用它來測試 priority_queue 是否為空白。

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

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a> priority_queue：： generic_container (STL/CLR) 

容器的泛型介面型別。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器介面卡類別的泛型介面。

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

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a> priority_queue：： generic_value (STL/CLR) 

要搭配容器的泛型介面使用的元素類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

型別描述型別的物件，此物件 `GValue` 描述與這個樣板容器類別的泛型介面搭配使用的預存專案值。  (`GValue` 是， `value_type` 或者 `value_type^` `value_type` 是 ref 類型。 ) 

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

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a> priority_queue：： get_container (STL/CLR) 

存取基礎容器。

### <a name="syntax"></a>語法

```cpp
container_type get_container();
```

### <a name="remarks"></a>備註

成員函式會傳回基礎容器。 您可以使用它來略過容器包裝函式所加諸的限制。

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

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a> priority_queue：： operator = (STL/CLR) 

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器介面卡。

### <a name="remarks"></a>備註

成員運算子會將 *右移* 至物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為 *right*中受控制序列的複本。

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

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a> priority_queue：:p op (STL/CLR) 

移除最高 proirity 的元素。

### <a name="syntax"></a>語法

```cpp
void pop();
```

### <a name="remarks"></a>備註

成員函式會移除受控制序列中最高優先順序的元素，此專案必須為非空白。 您可以使用它來將佇列縮短一回一個元素。

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

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a> priority_queue：:p riority_queue (STL/CLR) 

構造容器介面卡物件。

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

*續*<br/>
要複製的容器。

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*Pred*<br/>
受控制序列的順序述詞。

*對*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

函數：

`priority_queue();`

使用預設順序述詞，建立空的包裝容器。 您可以使用它來指定空的初始受控制序列，以及預設順序述詞。

函數：

`priority_queue(priority_queue<Value, Container>% right);`

使用順序述詞建立包裝的容器，該容器為的複本 `right.get_container()` `right.value_comp()` 。 您可以使用它來指定初始受控制序列，這是由佇列物件 *許可權*所控制之序列的複本（具有相同的順序述詞）。

函數：

`priority_queue(priority_queue<Value, Container>^ right);`

使用順序述詞建立包裝的容器，該容器為的複本 `right->get_container()` `right->value_comp()` 。 您可以使用它來指定初始受控制序列，其為佇列物件所控制之序列的複本 `*right` （具有相同的順序述詞）。

函數：

`explicit priority_queue(value_compare^ pred);`

使用順序述詞 *pred*建立空的包裝容器。 您可以使用它來指定空的初始受控制序列，以及指定的順序述詞。

函數：

`priority_queue(value_compare^ pred, container_type cont);`

使用指定的順序述詞，建立空的包裝容器（具有順序述詞 *pred*），然後推 *播您使用* 它來指定現有容器的初始受控制序列。

函數：

`template<typename InIt> priority_queue(InIt first, InIt last);`

使用預設順序述詞來建立空的包裝容器，然後將序列 [ `first` ， `last`) 推送。 您可以使用它，透過指定的順序述詞，從指定的 eqeuence 指定初始受控制序列。

函數：

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

使用排序述詞 *pred*建立空的已包裝容器，然後將序列 [ `first` ，) 推送 `last` 。 您可以使用它，透過指定的順序述詞，從指定的 seqeuence 指定初始受控制序列。

函數：

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

使用排序述詞 *pred*建立空的包裝容器，然後將 [ *接續* ] 和 [，) 的所有元素推入 `first` `last` 。 您可以使用它，透過指定的順序述詞，從現有的容器和指定的 seqeuence 指定初始受控制序列。

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

## <a name="priority_queuepush-stlclr"></a><a name="push"></a> priority_queue：:p ush (STL/CLR) 

新增元素。

### <a name="syntax"></a>語法

```cpp
void push(value_type val);
```

### <a name="remarks"></a>備註

成員函式會將具有值的元素插入 `val` 至受控制的序列中，並重新排序受控制的序列以維護堆積專業領域。 您可以使用它來將另一個元素新增至佇列。

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

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a> priority_queue：： reference (STL/CLR) 

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

型別描述對元素的參考。

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

## <a name="priority_queuesize-stlclr"></a><a name="size"></a> priority_queue：： size (STL/CLR) 

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[priority_queue：： empty (STL/CLR) ](#empty) `()` 。

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

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a> priority_queue：： size_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

型別描述非負的元素計數。

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

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a> priority_queue：： to_array (STL/CLR) 

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

成員函式會傳回陣列，其中包含受控制的序列。 您可以使用它，以陣列形式取得受控制序列的複本。

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

## <a name="priority_queuetop-stlclr"></a><a name="top"></a> priority_queue：： top (STL/CLR) 

存取最高優先順序的元素。

### <a name="syntax"></a>語法

```cpp
reference top();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列之 top (最高優先順序) 專案的參考，該專案必須為非空白。 您可以使用它來存取最高優先順序的元素（當您知道它存在時）。

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

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a> priority_queue：： top_item (STL/CLR) 

存取最高優先順序的元素。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列的 top (最高優先順序) 元素，而該專案必須為非空白。 您可以使用它來讀取或寫入最高優先順序的元素（當您知道它存在時）。

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

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a> priority_queue：： value_comp (STL/CLR) 

複製兩個項目的排序委派。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

成員函式會傳回排序委派，用來排序受控制的序列。 您會用它來比較兩個值。

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

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a> priority_queue：： value_compare (STL/CLR) 

兩個值的順序委派。

### <a name="syntax"></a>語法

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>備註

此類型是委派的同義字，可判斷第一個引數是否會在第二個引數之前排序。

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

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a> priority_queue：： value_type (STL/CLR) 

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *值*同義。

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
