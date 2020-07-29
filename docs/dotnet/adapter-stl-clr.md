---
title: adapter (STL/CLR)
ms.date: 06/15/2018
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
ms.openlocfilehash: 7730b5a8dbb8c92d85b4c8c5732657d28bf5b229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216436"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)

STL/CLR 標頭會 `<cliext/adapter>` 指定兩個範本類別（ `collection_adapter` 和 `range_adapter` ），以及範本 `make_collection` 函式。

## <a name="syntax"></a>語法

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>需求

**標頭：**\<cliext/adapter>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類別|說明|
|-----------|-----------------|
|[collection_adapter (STL/CLR)](#collection_adapter)|將基類程式庫（BCL）集合包裝為範圍。|
|[range_adapter (STL/CLR)](#range_adapter)|將範圍包裝為 BCL 集合。|

|函式|說明|
|--------------|-----------------|
|[make_collection (STL/CLR)](#make_collection)|使用反覆運算器配對建立範圍介面卡。|

## <a name="members"></a>成員

## <a name="collection_adapter-stlclr"></a><a name="collection_adapter"></a>collection_adapter （STL/CLR）

包裝 .NET 集合，以做為 STL/CLR 容器使用。 `collection_adapter`是描述簡單 STL/CLR 容器物件的範本類別。 它會包裝基類程式庫（BCL）介面，並傳回您用來操作受控制序列的反覆運算器配對。

### <a name="syntax"></a>語法

```cpp
template<typename Coll>
    ref class collection_adapter;

template<>
    ref class collection_adapter<
        System::Collections::ICollection>;
template<>
    ref class collection_adapter<
        System::Collections::IEnumerable>;
template<>
    ref class collection_adapter<
        System::Collections::IList>;
template<>
    ref class collection_adapter<
        System::Collections::IDictionary>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::ICollection<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IEnumerable<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IList<Value>>;
template<typename Key,
    typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IDictionary<Key, Value>>;
```

#### <a name="parameters"></a>參數

*序 coll*<br/>
已包裝之集合的型別。

### <a name="specializations"></a>特製化

|特製化|說明|
|--------------------|-----------------|
|IEnumerable|透過元素的序列。|
|ICollection|維護一組元素。|
|IList|維護元素的已排序群組。|
|IDictionary|維護一組 {key，value} 配對。|
|IEnumerable\<Value>|透過具類型專案的序列。|
|ICollection\<Value>|維護一組具類型的元素。|
|IList\<Value>|維護具類型元素的已排序群組。|
|IDictionary\<Value> |會維護一組具類型的 {key，value} 配對。|

### <a name="members"></a>成員

|類型定義|說明|
|---------------------|-----------------|
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[collection_adapter::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[collection_adapter::key_type (STL/CLR)](#key_type)|字典索引鍵的類型。|
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|字典值的類型。|
|[collection_adapter::reference (STL/CLR)](#reference)|項目的參考類型。|
|[collection_adapter::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[collection_adapter::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|說明|
|---------------------|-----------------|
|[collection_adapter::base (STL/CLR)](#base)|指定包裝的 BCL 介面。|
|[collection_adapter::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|結構介面卡物件。|
|[collection_adapter::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[collection_adapter::size (STL/CLR)](#size)|計算元素的數目。|
|[collection_adapter::swap (STL/CLR)](#swap)|交換兩個容器的內容。|

|運算子|描述|
|--------------|-----------------|
|[collection_adapter::operator= (STL/CLR)](#op_eq)|取代預存的 BCL 控制碼。|

### <a name="remarks"></a>備註

您可以使用這個樣板類別，將 BCL 容器操作為 STL/CLR 容器。 會 `collection_adapter` 儲存 BCL 介面的控制碼，進而控制元素的序列。 物件會傳回 `collection_adapter` `X` 一對輸入反覆運算器 `X.begin()` ，以及 `X.end()` 您用來依序流覽元素的。 部分特製化也可讓您撰寫 `X.size()` ，以判斷受控制序列的長度。

## <a name="collection_adapterbase-stlclr"></a><a name="base"></a>collection_adapter：： base （STL/CLR）

指定包裝的 BCL 介面。

### <a name="syntax"></a>語法

```cpp
Coll^ base();
```

### <a name="remarks"></a>備註

此成員函式會傳回已儲存的 BCL 介面控制碼。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_base.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);
    return (0);
    }
```

```Output
x x x x x x
base() same = True
```

## <a name="collection_adapterbegin-stlclr"></a><a name="begin"></a>collection_adapter：： begin （STL/CLR）

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

此成員函式會傳回輸入反覆運算器，指定受控制序列的第一個元素，或在空序列結尾以外的專案。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_begin.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mycoll::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
}
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="collection_adaptercollection_adapter-stlclr"></a><a name="collection_adapter_collection_adapter"></a>collection_adapter：： collection_adapter （STL/CLR）

結構介面卡物件。

### <a name="syntax"></a>語法

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>參數

*集合*<br/>
要包裝的 BCL 控制碼。

*再*<br/>
要複製的物件。

### <a name="remarks"></a>備註

此構造函式：

`collection_adapter();`

使用初始化預存控制碼 **`nullptr`** 。

此構造函式：

`collection_adapter(collection_adapter<Coll>% right);`

使用 `right.` [collection_adapter：： BASE （STL/CLR）](../dotnet/collection-adapter-base-stl-clr.md)初始化預存控制碼 `()` 。

此構造函式：

`collection_adapter(collection_adapter<Coll>^ right);`

使用 `right->` [collection_adapter：： BASE （STL/CLR）](../dotnet/collection-adapter-base-stl-clr.md)初始化預存控制碼 `()` 。

此構造函式：

`collection_adapter(Coll^ collection);`

使用初始化預存控制碼 `collection` 。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');

    // construct an empty container
    Mycoll c1;
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);

    // construct with a handle
    Mycoll c2(%d6x);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mycoll c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mycoll c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
base() null = True
x x x x x x
x x x x x x
x x x x x x
```

## <a name="collection_adapterdifference_type-stlclr"></a><a name="difference_type"></a>collection_adapter：:d ifference_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述帶正負號的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_difference_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mycoll::difference_type diff = 0;
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
}
```

```Output
a b c
end()-begin() = 3
```

## <a name="collection_adapterend-stlclr"></a><a name="end"></a>collection_adapter：： end （STL/CLR）

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

此成員函式會傳回指向受控制序列結尾之外的輸入反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_end.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapteriterator-stlclr"></a><a name="iterator"></a>collection_adapter：： iterator （STL/CLR）

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型的物件 `T1` ，可做為受控制序列的輸入反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_iterator.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapterkey_type-stlclr"></a><a name="key_type"></a>collection_adapter：： key_type （STL/CLR）

字典索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

在或的特製化中，此類型是樣板參數的同義字 `Key` ， `IDictionary` `IDictionary<Value>` 否則不會定義。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_key_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adaptermapped_type-stlclr"></a><a name="mapped_type"></a>collection_adapter：： mapped_type （STL/CLR）

字典值的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>備註

在或的特製化中，此類型是樣板參數的同義字 `Value` ， `IDictionary` `IDictionary<Value>` 否則不會定義。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_mapped_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adapteroperator-stlclr"></a><a name="op_eq"></a>collection_adapter：： operator = （STL/CLR）

取代預存的 BCL 控制碼。

### <a name="syntax"></a>語法

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要複製的介面卡。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 **`*this`** 。 您可以使用它，以*右側*儲存的 bcl 控制碼複本來取代儲存的 bcl 控制碼。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mycoll c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="collection_adapterreference-stlclr"></a><a name="reference"></a>collection_adapter：： reference （STL/CLR）

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述專案的參考。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_reference.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
    {   // get a reference to an element
        Mycoll::reference ref = *it;
        System::Console::Write("{0} ", ref);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adaptersize-stlclr"></a><a name="size"></a>collection_adapter：： size （STL/CLR）

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 它不會在或的特製化中定義 `IEnumerable` `IEnumerable<Value>` 。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_size.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adaptersize_type-stlclr"></a><a name="size_type"></a>collection_adapter：： size_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_size_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    Mycoll::size_type size = c1.size();
    System::Console::WriteLine("size() = {0}", size);
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adapterswap-stlclr"></a><a name="swap"></a>collection_adapter：： swap （STL/CLR）

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

此成員函式會在和 right 之間交換已儲存的 BCL 控點 **`*this`** 。 *right*

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="collection_adaptervalue_type-stlclr"></a><a name="value_type"></a>collection_adapter：： value_type （STL/CLR）

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數*值*同義，如果存在於特製化中，則為否則，它是的同義字 `System::Object^` 。

### <a name="example"></a>範例

```cpp
// cliext_collection_adapter_value_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display contents "a b c" using value_type
    for (Mycoll::iterator it = c1.begin();
        it != c1.end(); ++it)
    {   // store element in value_type object
        Mycoll::value_type val = *it;

        System::Console::Write("{0} ", val);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="make_collection-stlclr"></a><a name="make_collection"></a>make_collection （STL/CLR）

`range_adapter`從反覆運算器配對進行。

### <a name="syntax"></a>語法

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>參數

*Iter*<br/>
已包裝反覆運算器的類型。

*first*<br/>
要包裝的第一個反覆運算器。

*last*<br/>
要包裝的第二個反覆運算器。

### <a name="remarks"></a>備註

此範本函式會傳回 `gcnew range_adapter<Iter>(first, last)`。 您可以使用它來 `range_adapter<Iter>` 從一對反覆運算器中建立物件。

### <a name="example"></a>範例

```cpp
// cliext_make_collection.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in d1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Collections::ICollection^ p1 =
        cliext::make_collection(d1.begin(), d1.end());
    System::Console::WriteLine("Count = {0}", p1->Count);
    System::Console::WriteLine("IsSynchronized = {0}",
        p1->IsSynchronized);
    System::Console::WriteLine("SyncRoot not nullptr = {0}",
        p1->SyncRoot != nullptr);

    // copy the sequence
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);

    a1[0] = L'|';
    p1->CopyTo(a1, 1);
    a1[4] = L'|';
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
Count = 3
IsSynchronized = False
SyncRoot not nullptr = True
| a b c |
```

## <a name="range_adapter-stlclr"></a><a name="range_adapter"></a>range_adapter （STL/CLR）

此樣板類別會包裝一對用來執行數個基類庫（BCL）介面的反覆運算器。 您可以使用 range_adapter 來操作 STL/CLR 範圍，如同它是 BCL 集合。

### <a name="syntax"></a>語法

```cpp
template<typename Iter>
    ref class range_adapter
        :   public
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<Value>,
        System::Collections::Generic::ICollection<Value>
    { ..... };
```

#### <a name="parameters"></a>參數

*Iter*<br/>
與包裝的反覆運算器相關聯的類型。

### <a name="members"></a>成員

|成員函式|說明|
|---------------------|-----------------|
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|結構介面卡物件。|

|運算子|說明|
|--------------|-----------------|
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|取代預存反覆運算器配對。|

### <a name="interfaces"></a>介面

|介面|說明|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|逐一查看集合中的元素。|
|<xref:System.Collections.ICollection>|維護一組元素。|
|<xref:System.Collections.Generic.IEnumerable%601>|逐一查看集合中具類型的元素。|
|<xref:System.Collections.Generic.ICollection%601>|維護一組具類型的元素。|

### <a name="remarks"></a>備註

Range_adapter 會儲存一對反覆運算器，然後再將專案序列分隔。 物件會執行四個 BCL 介面，讓您依序逐一查看元素。 您可以使用此範本類別來操作 STL/CLR 範圍，就像 BCL 容器一樣。

## <a name="range_adapteroperator-stlclr"></a><a name="range_adapter_op_eq"></a>range_adapter：： operator = （STL/CLR）

取代預存反覆運算器配對。

### <a name="syntax"></a>語法

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要複製的介面卡。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 **`*this`** 。 您可以使用它來取代預存反覆運算器配對，並在*右邊*加上預存反覆運算器配對的複本。

### <a name="example"></a>範例

```cpp
// cliext_range_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Myrange c1(d1.begin(), d1.end());

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myrange c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
a b c
```

## <a name="range_adapterrange_adapter-stlclr"></a><a name="range_adapter_range_adapter"></a>range_adapter：： range_adapter （STL/CLR）

結構介面卡物件。

### <a name="syntax"></a>語法

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>參數

*first*<br/>
要包裝的第一個反覆運算器。

*last*<br/>
要包裝的第二個反覆運算器。

*再*<br/>
要複製的物件。

### <a name="remarks"></a>備註

此構造函式：

`range_adapter();`

使用預設的結構化反覆運算器，初始化預存反覆運算器配對。

此構造函式：

`range_adapter(range_adapter<Iter>% right);`

複製儲存在*右方*的配對，初始化預存反覆運算器配對。

此構造函式：

`range_adapter(range_adapter<Iter>^ right);`

藉由複製儲存在中的配對，初始化預存反覆運算器配對 `*right` 。

此構造函式：

`range_adapter(Iter^ first, last);`

以*first*和*last*初始化預存反覆運算器配對。

### <a name="example"></a>範例

```cpp
// cliext_range_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // construct an empty adapter
    Myrange c1;

    // construct with an iterator pair
    Myrange c2(d1.begin(), d1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another adapter
    Myrange c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying an adapter handle
    Myrange c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
a b c
a b c
```
