---
title: stack (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
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
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
ms.openlocfilehash: 5f5cfbb4f6125c1c72550018735b377e1507ab08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214879"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)

此樣板類別所描述的物件可控制具有後進先出存取權的變動長度元素序列。 您可以使用容器介面卡 `stack` ，以向下推堆疊的形式來管理基礎容器。

在下面的描述中，與 `GValue` *值*相同，除非後者是 ref 類型，在此情況下為 `Value^` 。 同樣地，與 `GContainer` *容器*相同，除非後者是 ref 類型，在此情況下為 `Container^` 。

## <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    ref class stack
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>參數

*ReplTest1*<br/>
受控制序列中項目的類型。

*容器*<br/>
基礎容器的類型。

## <a name="requirements"></a>需求

**標頭：**\<cliext/stack>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|說明|
|---------------------|-----------------|
|[stack::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[stack::container_type (STL/CLR)](#container_type)|基礎容器的類型。|
|[stack::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[stack::generic_container (STL/CLR)](#generic_container)|容器介面卡的泛型介面類別型。|
|[stack::generic_value (STL/CLR)](#generic_value)|適用于容器介面卡之泛型介面的元素類型。|
|[stack::reference (STL/CLR)](#reference)|項目的參考類型。|
|[stack::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[stack::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|說明|
|---------------------|-----------------|
|[stack::assign (STL/CLR)](#assign)|取代所有項目。|
|[stack::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[stack::get_container (STL/CLR)](#get_container)|存取基礎容器。|
|[stack::pop (STL/CLR)](#pop)|移除最後一個元素。|
|[stack::push (STL/CLR)](#push)|加入新的最後一個元素。|
|[stack::size (STL/CLR)](#size)|計算元素的數目。|
|[stack::stack (STL/CLR)](#stack)|建構容器物件。|
|[stack::top (STL/CLR)](#top)|存取最後一個項目。|
|[stack::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|

|屬性|說明|
|--------------|-----------------|
|[stack::top_item (STL/CLR)](#top_item)|存取最後一個項目。|

|運算子|說明|
|--------------|-----------------|
|[stack::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[operator！ = （stack）（STL/CLR）](#op_neq)|判斷物件是否 `stack` 不等於另一個 `stack` 物件。|
|[運算子< （stack）（STL/CLR）](#op_lt)|判斷 `stack` 物件是否小於另一個 `stack` 物件。|
|[運算子<= （stack）（STL/CLR）](#op_lteq)|判斷 `stack` 物件是否小於或等於另一個 `stack` 物件。|
|[operator== (stack) (STL/CLR)](#op_eq)|判斷 `stack` 物件是否等於另一個 `stack` 物件。|
|[運算子> （stack）（STL/CLR）](#op_gt)|判斷 `stack` 物件是否大於另一個 `stack` 物件。|
|[運算子>= （stack）（STL/CLR）](#op_gteq)|判斷 `stack` 物件是否大於或等於另一個 `stack` 物件。|

## <a name="interfaces"></a>介面

|介面|說明|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|IStack\<Value, Container>|維護一般容器介面卡。|

## <a name="remarks"></a>備註

物件會透過*容器*類型的基礎容器來配置和釋放其所控制之序列的儲存體，以儲存*值*元素並隨需成長。 物件會限制只能推送和彈出最後一個專案的存取，並執行後進先出的佇列（也稱為 LIFO 佇列或堆疊）。

## <a name="members"></a>成員

## <a name="stackassign-stlclr"></a><a name="assign"></a>stack：： assign （STL/CLR）

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要插入的容器介面卡。

### <a name="remarks"></a>備註

成員函式會指派 `right.get_container()` 給基礎容器。 您可以使用它來變更堆疊的完整內容。

### <a name="example"></a>範例

```cpp
// cliext_stack_assign.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Mystack c2;
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

## <a name="stackconst_reference-stlclr"></a><a name="const_reference"></a>stack：： const_reference （STL/CLR）

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

此類型描述專案的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_stack_const_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mystack::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="stackcontainer_type-stlclr"></a><a name="container_type"></a>stack：： container_type （STL/CLR）

基礎容器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Container* 同義。

### <a name="example"></a>範例

```cpp
// cliext_stack_container_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="stackdifference_type-stlclr"></a><a name="difference_type"></a>stack：:d ifference_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能為負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_stack_difference_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Mystack::difference_type diff = c1.size();
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

## <a name="stackempty-stlclr"></a><a name="empty"></a>stack：： empty （STL/CLR）

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[stack：： size （STL/CLR）](../dotnet/stack-size-stl-clr.md) `() == 0` 。 您可以使用它來測試堆疊是否為空的。

### <a name="example"></a>範例

```cpp
// cliext_stack_empty.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stackgeneric_container-stlclr"></a><a name="generic_container"></a>stack：： generic_container （STL/CLR）

容器介面卡的泛型介面類別型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::IStack<Value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器介面卡類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_stack_generic_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
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

## <a name="stackgeneric_value-stlclr"></a><a name="generic_value"></a>stack：： generic_value （STL/CLR）

要與容器的泛型介面搭配使用之元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

此類型描述類型的物件 `GValue` ，其描述要與這個樣板容器類別的泛型介面搭配使用的預存元素值。 （ `GValue` `value_type` `value_type^` 如果是 ref 型別，則為或 `value_type` ）。

### <a name="example"></a>範例

```cpp
// cliext_stack_generic_value.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in reverse using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mystack::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
c b a
```

## <a name="stackget_container-stlclr"></a><a name="get_container"></a>stack：： get_container （STL/CLR）

存取基礎容器。

### <a name="syntax"></a>語法

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>備註

此成員函式會傳回基礎容器的控制碼。 您可以使用它來略過容器包裝函式所加諸的限制。

### <a name="example"></a>範例

```cpp
// cliext_stack_get_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="stackoperator-stlclr"></a><a name="op_as"></a>stack：： operator = （STL/CLR）

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
stack <Value, Container>% operator=(stack <Value, Container>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要複製的容器介面卡。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為*右邊*的受控制序列複本。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_as.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="stackpop-stlclr"></a><a name="pop"></a>stack：:p op （STL/CLR）

移除最後一個元素。

### <a name="syntax"></a>語法

```cpp
void pop();
```

### <a name="remarks"></a>備註

此成員函式會移除受控制序列中的最後一個專案，此專案必須為非空白。 您可以使用它來縮短堆疊上一個元素的堆疊。

### <a name="example"></a>範例

```cpp
// cliext_stack_pop.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b
```

## <a name="stackpush-stlclr"></a><a name="push"></a>stack：:p ush （STL/CLR）

加入新的最後一個元素。

### <a name="syntax"></a>語法

```cpp
void push(value_type val);
```

### <a name="remarks"></a>備註

成員函式會將具有值的元素插入 `val` 受控制序列的結尾。 您可以使用它將另一個元素附加至堆疊。

### <a name="example"></a>範例

```cpp
// cliext_stack_push.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stackreference-stlclr"></a><a name="reference"></a>stack：： reference （STL/CLR）

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述專案的參考。

### <a name="example"></a>範例

```cpp
// cliext_stack_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify top of stack and redisplay
    Mystack::reference ref = c1.top();
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

## <a name="stacksize-stlclr"></a><a name="size"></a>stack：： size （STL/CLR）

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[stack：： empty （STL/CLR）](../dotnet/stack-empty-stl-clr.md) `()` 。

### <a name="example"></a>範例

```cpp
// cliext_stack_size.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stacksize_type-stlclr"></a><a name="size_type"></a>stack：： size_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_stack_size_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Mystack::size_type diff = c1.size();
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

## <a name="stackstack-stlclr"></a><a name="stack"></a>stack：： stack （STL/CLR）

建立容器介面卡物件。

### <a name="syntax"></a>語法

```cpp
stack();
stack(stack<Value, Container>% right);
stack(stack<Value, Container>^ right);
explicit stack(container_type% wrapped);
```

#### <a name="parameters"></a>參數

*再*<br/>
要複製的物件。

*換*<br/>
要使用的已包裝容器。

### <a name="remarks"></a>備註

此構造函式：

`stack();`

建立空的包裝容器。 您可以使用它來指定空的初始受控制序列。

此構造函式：

`stack(stack<Value, Container>% right);`

建立包裝的容器，其為的複本 `right.get_container()` 。 您可以使用它來指定初始受控制序列，這是堆疊物件*許可權*所控制之序列的複本。

此構造函式：

`stack(stack<Value, Container>^ right);`

建立包裝的容器，其為的複本 `right->get_container()` 。 您可以使用它來指定初始受控制序列，這是堆疊物件所控制之序列的複本 `*right` 。

此構造函式：

`explicit stack(container_type% wrapped);`

使用*包裝*為包裝容器的現有容器。 您可以使用它來從現有的容器中建立堆疊。

### <a name="example"></a>範例

```cpp
// cliext_stack_construct.cpp
// compile with: /clr
#include <cliext/stack>
#include <cliext/vector>

typedef cliext::stack<wchar_t> Mystack;
typedef cliext::vector<wchar_t> Myvector;
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;
int main()
    {
// construct an empty container
    Mystack c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Myvector v2(5, L'x');
    Mystack_vec c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Mystack_vec c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Mystack_vec c4(%c2);
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

## <a name="stackto_array-stlclr"></a><a name="to_array"></a>stack：： to_array （STL/CLR）

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

此成員函式會傳回陣列，其中包含受控制的序列。 您可以用它來取得陣列表單中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_stack_to_array.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stacktop-stlclr"></a><a name="top"></a>stack：： top （STL/CLR）

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
reference top();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制序列之最後一個元素的參考，該專案必須為非空白。 當您知道它是否存在時，您可以使用它來存取最後一個元素。

### <a name="example"></a>範例

```cpp
// cliext_stack_top.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

```Output
a b c
top() = c
a b x
```

## <a name="stacktop_item-stlclr"></a><a name="top_item"></a>stack：： top_item （STL/CLR）

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type top_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列中的最後一個專案，其必須為非空白。 當您知道最後一個元素存在時，就可以使用它來讀取或寫入它。

### <a name="example"></a>範例

```cpp
// cliext_stack_top_item.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
top_item = c
a b x
```

## <a name="stackvalue_type-stlclr"></a><a name="value_type"></a>stack：： value_type （STL/CLR）

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數*值*同義。

### <a name="example"></a>範例

```cpp
// cliext_stack_value_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mystack::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="operator-stack-stlclr"></a><a name="op_neq"></a>operator！ = （stack）（STL/CLR）

堆疊不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator!=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(left == right)` 。 您可以使用它來測試當兩個堆疊是以元素進行比較時，是否將*left*與*right*排序。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_ne.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorlt-stack-stlclr"></a><a name="op_lt"></a>operator &lt; （stack）（STL/CLR）

堆疊小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator<(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果的最低位置也為 true，則運算子函數 `i` 會傳回 true `!(right[i] < left[i])` `left[i] < right[i]` 。 否則，它會傳回 `left->` [stack：： size （STL/CLR）](../dotnet/stack-size-stl-clr.md) ， `() <` `right->size()` 您可以用它*left*來測試當兩個堆疊是以元素進行比較時，是否要在*右邊*排序。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_lt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorlt-stack-stlclr"></a><a name="op_lteq"></a>operator &lt; = （stack）（STL/CLR）

堆疊小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator<=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(right < left)` 。 您可以使用它來測試當兩個堆疊是以元素進行比較時 *，是否要*在*右*向後排序。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_le.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operator-stack-stlclr"></a><a name="op_eq"></a>operator = = （stack）（STL/CLR）

堆疊相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator==(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

只有當*left*和*right*所控制的序列具有相同的長度，且每個位置都有相同的時，運算子函數才會傳回 true `i` `left[i] ==` `right[i]` 。 您可以使用它來測試當兩個堆疊是以元素進行比較時，*左側*是否與*右*排序相同。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_eq.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorgt-stack-stlclr"></a><a name="op_gt"></a>operator &gt; （stack）（STL/CLR）

堆疊大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator>(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `right` `<` `left` 。 您可以使用它來測試當兩個堆疊是以元素進行比較時 *，是否要*在*右*向後排序。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_gt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorgt-stack-stlclr"></a><a name="op_gteq"></a>operator &gt; = （stack）（STL/CLR）

堆疊大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value,
    typename Container>
    bool operator>=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(left < right)` 。 您可以使用它來測試當兩個堆疊是以元素進行比較時 *，是否要*在*右方*之前排序。

### <a name="example"></a>範例

```cpp
// cliext_stack_operator_ge.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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
