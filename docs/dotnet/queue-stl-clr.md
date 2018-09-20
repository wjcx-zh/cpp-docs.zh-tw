---
title: 佇列 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::queue::assign
- cliext::queue::back
- cliext::queue::back_item
- cliext::queue::const_reference
- cliext::queue::container_type
- cliext::queue::difference_type
- cliext::queue::empty
- cliext::queue::front
- cliext::queue::front_item
- cliext::queue::generic_container
- cliext::queue::generic_value
- cliext::queue::get_container
- cliext::queue::operator=
- cliext::queue::pop
- cliext::queue::push
- cliext::queue::queue
- cliext::queue::reference
- cliext::queue::size
- cliext::queue::size_type
- cliext::queue::to_array
- cliext::queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- queue member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e3339a678e7d2443702995d09837c7efbb40005d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375716"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)

此範本類別描述控制不同長度序列的項目具有先進先出 」 存取權的物件。 您使用的容器配接器`queue`管理為佇列基礎容器。

下列描述中`GValue`等同*值*後者是 ref 型別，除非在此情況下是`Value^`。 同樣地，`GContainer`等同*容器*後者是 ref 型別，除非在此情況下是`Container^`。

## <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    ref class queue
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>參數

*值*<br/>
受控制序列中項目的類型。

*容器*<br/>
基礎容器的類型。

## <a name="requirements"></a>需求

**標頭：** \<cliext/佇列 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[queue::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[queue::container_type (STL/CLR)](#container_type)|基礎容器的類型。|
|[queue::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[queue::generic_container (STL/CLR)](#generic_container)|容器配接器的泛型介面型別。|
|[queue::generic_value (STL/CLR)](#generic_value)|容器配接器的泛型介面的項目型別。|
|[queue::reference (STL/CLR)](#reference)|項目的參考類型。|
|[queue::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[queue::value_type (STL/CLR)](#value_type)|元素的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[queue::assign (STL/CLR)](#assign)|取代所有項目。|
|[queue::back (STL/CLR)](#back)|存取最後一個項目。|
|[queue::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[queue::front (STL/CLR)](#front)|存取第一個項目。|
|[queue::get_container (STL/CLR)](#get_container)|存取基礎容器。|
|[queue::pop (STL/CLR)](#pop)|移除第一個項目。|
|[queue::push (STL/CLR)](#push)|加入新的最後一個項目。|
|[queue::queue (STL/CLR)](#queue)|建構容器物件。|
|[queue::size (STL/CLR)](#size)|計算元素的數目。|
|[queue::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|

|屬性|描述|
|--------------|-----------------|
|[queue::back_item (STL/CLR)](#back_item)|存取最後一個項目。|
|[queue::front_item (STL/CLR)](#front_item)|存取第一個項目。|

|運算子|描述|
|--------------|-----------------|
|[queue::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[operator!= (queue) (STL/CLR)](#op_neq)|決定是否`queue`物件是否不等於另一個`queue`物件。|
|[operator< (queue) (STL/CLR)](#op_lt)|決定是否`queue`物件是否小於另一個`queue`物件。|
|[operator<= (queue) (STL/CLR)](#op_lteq)|決定是否`queue`物件是否小於或等於另一個`queue`物件。|
|[operator== (queue) (STL/CLR)](#op_eq)|決定是否`queue`物件是否等於另一個`queue`物件。|
|[operator> (queue) (STL/CLR)](#op_gt)|決定是否`queue`物件是否大於另一個`queue`物件。|
|[operator>= (queue) (STL/CLR)](#op_gteq)|決定是否`queue`物件是否大於或等於另一個`queue`物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|重複的物件。|
|IQueue\<值、 容器 >|維護泛型容器配接器。|

## <a name="remarks"></a>備註

物件，配置並釋放它透過基礎的容器，型別所控制之序列的儲存體`Container`，儲存`Value`項目並視需要成長。 物件只能存取只按第一個項目，並拉出的最後一個項目，實作先進先出佇列 （也稱為 FIFO 佇列中或只是佇列）。

## <a name="members"></a>成員

## <a name="assign"></a> queue::assign (STL/CLR)

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要插入的容器配接器。

### <a name="remarks"></a>備註

此成員函式會指派`right.get_container()`至基礎容器。 您可以使用它來變更佇列的整個內容。

### <a name="example"></a>範例

```cpp
// cliext_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Myqueue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="back"></a> queue:: back (STL/CLR)

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
reference back();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制的序列必須為非空白的最後一個元素的參考。 您可以使用它來存取的最後一個元素，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_queue_back.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="back_item"></a> queue::back_item (STL/CLR)

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性存取受控制的序列必須為非空白的最後一個元素。 您可以使用它來讀取或寫入的最後一個元素，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_queue_back_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="const_reference"></a> queue::const_reference (STL/CLR)

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

此類型描述項目的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Myqueue::const_reference cref = c1.front();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="container_type"></a> queue:: container_type (STL/CLR)

基礎容器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Container`的同義字。

### <a name="example"></a>範例

```cpp
// cliext_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Myqueue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="difference_type"></a> queue::difference_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能是負數的項目計數。

### <a name="example"></a>範例

```cpp
// cliext_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Myqueue::difference_type diff = c1.size();
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
a b c
pushing 2 = -2
popping 3 = 3
```

## <a name="empty"></a> queue:: empty (STL/CLR)

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md)`() == 0`。 您可以使用它來測試是否是空的佇列。

### <a name="example"></a>範例

```cpp
// cliext_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="front"></a> queue:: front (STL/CLR)

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
reference front();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制的序列必須為非空白的第一個元素的參考。 您可以使用它來存取第一個項目中，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_queue_front.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="front_item"></a> queue::front_item (STL/CLR)

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>備註

屬性存取受控制的序列必須為非空白的第一個元素。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。

### <a name="example"></a>範例

```cpp
// cliext_queue_front_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter last item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="generic_container"></a> queue::generic_container (STL/CLR)

容器配接器的泛型介面型別。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::IQueue<Value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器配接器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myqueue::generic_container^ gc1 = %c1;
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
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_value"></a> queue::generic_value (STL/CLR)

使用容器的泛型介面的項目型別。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

此類型所描述型別的物件`GValue`，描述與此範本的容器類別的泛型介面使用的預存的項目值。 (`GValue`可能`value_type`或是`value_type^`如果`value_type`是 ref 型別。)

### <a name="example"></a>範例

```cpp
// cliext_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Myqueue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Myqueue::generic_value elem = gc1->front();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c
```

## <a name="get_container"></a> queue::get_container (STL/CLR)

存取基礎容器。

### <a name="syntax"></a>語法

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>備註

此成員函式會傳回基礎容器。 您可以使用它來略過由容器包裝函式所加諸的限制。

### <a name="example"></a>範例

```cpp
// cliext_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="op_as"></a> queue::operator = (STL/CLR)

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
queue <Value, Container>% operator=(queue <Value, Container>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要複製的容器配接器。

### <a name="remarks"></a>備註

成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代受控制的序列中的受控制序列的複本*右*。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop"></a> queue:: pop (STL/CLR)

移除最後一個項目。

### <a name="syntax"></a>語法

```cpp
void pop();
```

### <a name="remarks"></a>備註

此成員函式中移除受控制的序列必須為非空白的最後一個元素。 您可以使用它來縮短佇列後端的一個項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
b c
```

## <a name="push"></a> queue:: push (STL/CLR)

加入新的最後一個項目。

### <a name="syntax"></a>語法

```cpp
void push(value_type val);
```

### <a name="remarks"></a>備註

此成員函式將值的項目`val`佇列的結尾。 您可以使用它來將項目附加至佇列。

### <a name="example"></a>範例

```cpp
// cliext_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="queue"></a> queue:: queue (STL/CLR)

建構容器配接器物件。

### <a name="syntax"></a>語法

```cpp
queue();
queue(queue<Value, Container>% right);
queue(queue<Value, Container>^ right);
explicit queue(container_type% wrapped);
```

#### <a name="parameters"></a>參數

*right*<br/>
要複製的物件。

*換行*<br/>
若要使用的已包裝的容器。

### <a name="remarks"></a>備註

建構函式：

`queue();`

建立空的包裝的容器。 您可以使用它來指定空的初始受控制的序列。

建構函式：

`queue(queue<Value, Container>% right);`

建立包裝的容器，是一份`right.get_container()`。 您使用它來指定初始受控制的序列的佇列物件所控制之序列的複本*右*。

建構函式：

`queue(queue<Value, Container>^ right);`

建立包裝的容器，是一份`right->get_container()`。 您使用它來指定初始受控制的序列的佇列物件所控制的序列複本`*right`。

建構函式：

`explicit queue(container_type wrapped);`

使用現有的容器*包裝*做為包裝的容器。 您可以使用它來建構佇列，以從現有的容器。

### <a name="example"></a>範例

```cpp
// cliext_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/list>

typedef cliext::queue<wchar_t> Myqueue;
typedef cliext::list<wchar_t> Mylist;
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;
int main()
    {
// construct an empty container
    Myqueue c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Mylist v2(5, L'x');
    Myqueue_list c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myqueue_list c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Myqueue_list c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
x x x x x
x x x x x
x x x x x
```

## <a name="reference"></a> queue::reference (STL/CLR)

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述項目的參考。

### <a name="example"></a>範例

```cpp
// cliext_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify back of queue and redisplay
    Myqueue::reference ref = c1.back();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b x
```

## <a name="size"></a> queue:: size (STL/CLR)

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列的項目數。 如果您在意順序是否有非零值的大小，請參閱[queue:: empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)`()`。

### <a name="example"></a>範例

```cpp
// cliext_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="size_type"></a> queue:: size_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述的非負數的項目計數。

### <a name="example"></a>範例

```cpp
// cliext_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myqueue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
a b c
size difference = 2
```

## <a name="to_array"></a> queue::to_array (STL/CLR)

將受控制的序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

此成員函式會傳回包含之受控制的序列的陣列。 您可以使用它來取得陣列形式中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c d
a b c
```

## <a name="value_type"></a> queue:: value_type (STL/CLR)

元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

類型是範本參數的同義字*值*。

### <a name="example"></a>範例

```cpp
// cliext_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Myqueue::value_type val = c1.front();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> 運算子 ！ = （佇列） (STL/CLR)

佇列不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator!=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回`!(left == right)`。 您會使用它來測試是否*左*未經過排序相同*右*當兩個佇列都是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_ne.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> 運算子&lt;（佇列） (STL/CLR)

佇列小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator<(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式傳回則為 true，最低的位置`i`為其`!(right[i] < left[i])`也雖說， `left[i] < right[i]`。 否則，它會傳回`left->` [queue:: size (STL/CLR)](../dotnet/queue-size-stl-clr.md) `() <` `right->size()`使用它來測試是否*左*排序之前*右*當兩個佇列是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_lt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> 運算子&lt;= （佇列） (STL/CLR)

佇列小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator<=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回`!(right < left)`。 您會使用它來測試是否*左*未經過排序之後*右*當兩個佇列都是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_le.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> 運算子 = = （佇列） (STL/CLR)

佇列相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator==(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 true 所控制的序列時，才*左*並*右*具有相同的長度和每個位置`i`， `left[i] ==` `right[i]`。 您會使用它來測試是否*左*排序相同*右*當兩個佇列都是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_eq.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> 運算子&gt;（佇列） (STL/CLR)

大於比較的佇列。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator>(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回`right` `<` `left`。 您會使用它來測試是否*左*經過排序之後*右*當兩個佇列都是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_gt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> 運算子&gt;= （佇列） (STL/CLR)

排入佇列 大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator>=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回`!(left < right)`。 您會使用它來測試是否*左*未經過排序再*右*當兩個佇列都是由項目相比較的項目。

### <a name="example"></a>範例

```cpp
// cliext_queue_operator_ge.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```