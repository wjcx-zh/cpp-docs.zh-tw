---
title: adapter (STL/CLR)
ms.date: 06/15/2018
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
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
ms.openlocfilehash: d5c554439d9bb418b9b62484ee10cd6917cf1777
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436125"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)

STL/CLR 標頭`<cliext/adapter>`指定兩個範本類別 (`collection_adapter`並`range_adapter`)，並使用範本函式`make_collection`。

## <a name="syntax"></a>語法

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>需求

**標頭：** \<cliext/配接器 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類別|描述|
|-----------|-----------------|
|[collection_adapter (STL/CLR)](#collection_adapter)|包裝為一個範圍的基底類別庫 (BCL) 集合。|
|[range_adapter (STL/CLR)](#range_adapter)|包裝為 BCL 集合的範圍。|

|功能|描述|
|--------------|-----------------|
|[make_collection (STL/CLR)](#make_collection)|建立使用迭代器配對範圍配接器。|

## <a name="members"></a>成員

## <a name="collection_adapter"></a> collection_adapter (STL/CLR)

包裝 STL/CLR 容器做為.NET 集合。 A`collection_adapter`是範本類別描述一個簡單的 STL/CLR 容器物件。 它會包裝基底類別庫 (BCL) 介面，並傳回您用來管理受控制的序列的迭代器組。

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

*Coll*<br/>
已包裝的集合型別。

### <a name="specializations"></a>特製化

|特製化|描述|
|--------------------|-----------------|
|IEnumerable|透過項目序列。|
|ICollection|會維護一組項目。|
|IList|會維護項目已排序的群組。|
|IDictionary|維護一組 {索引鍵，值} 組。|
|IEnumerable\<值 >|透過具類型的項目序列。|
|ICollection\<值 >|會維護一組具類型的項目。|
|IList\<值 >|會維護排序的群組的具類型的項目。|
|IDictionary\<值 >|會維護一組具型別 {索引鍵，值} 組。|

### <a name="members"></a>成員

|類型定義|描述|
|---------------------|-----------------|
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[collection_adapter::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[collection_adapter::key_type (STL/CLR)](#key_type)|字典索引鍵的類型。|
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|字典值的型別。|
|[collection_adapter::reference (STL/CLR)](#reference)|項目的參考類型。|
|[collection_adapter::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[collection_adapter::value_type (STL/CLR)](#value_type)|元素的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[collection_adapter::base (STL/CLR)](#base)|將指定的已包裝的 BCL 介面。|
|[collection_adapter::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|建構的配置器物件。|
|[collection_adapter::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[collection_adapter::size (STL/CLR)](#size)|計算元素的數目。|
|[collection_adapter::swap (STL/CLR)](#swap)|交換兩個容器的內容。|

|運算子|描述|
|--------------|-----------------|
|[collection_adapter::operator= (STL/CLR)](#op_eq)|取代預存的 BCL 控制代碼。|

### <a name="remarks"></a>備註

您可以使用此範本類別來操作 STL/CLR 容器的 BCL 容器。 `collection_adapter`儲存至 BCL 介面，進而控制序列的項目控制代碼。 A`collection_adapter`物件`X`會傳回輸入迭代器的一組`X.begin()`和`X.end()`，使用中訂單的項目，請瀏覽。 部分特製化也可讓您撰寫`X.size()`來判斷受控制序列的長度。

## <a name="base"></a> collection_adapter::base (STL/CLR)

將指定的已包裝的 BCL 介面。

### <a name="syntax"></a>語法

```cpp
Coll^ base();
```

### <a name="remarks"></a>備註

此成員函式會傳回預存的 BCL 介面控制代碼。

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

## <a name="begin"></a> collection_adapter::begin (STL/CLR)

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

此成員函式會傳回指定之受控制的序列，或只是超出空序列結尾的第一個元素的輸入迭代器。

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

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)

建構的配置器物件。

### <a name="syntax"></a>語法

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>參數

*collection*<br/>
BCL 換行控制代碼。

*right*<br/>
要複製的物件。

### <a name="remarks"></a>備註

建構函式：

`collection_adapter();`

初始化具有預存的控制代碼`nullptr`。

建構函式：

`collection_adapter(collection_adapter<Coll>% right);`

初始化具有預存的控制代碼`right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。

建構函式：

`collection_adapter(collection_adapter<Coll>^ right);`

初始化具有預存的控制代碼`right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`。

建構函式：

`collection_adapter(Coll^ collection);`

初始化具有預存的控制代碼`collection`。

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

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述的帶正負號的項目計數。

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

## <a name="end"></a> collection_adapter::end (STL/CLR)

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函式會傳回輸入迭代器，指向超過受控制序列的結尾。

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

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定型別的物件`T1`，可做為受控制序列的輸入迭代器。

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

## <a name="key_type"></a> collection_adapter::key_type (STL/CLR)

字典索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

類型是範本參數的同義字`Key`中的特製化`IDictionary`或`IDictionary<Value>`; 否則為未定義。

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

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)

字典值的型別。

### <a name="syntax"></a>語法

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>備註

類型是範本參數的同義字`Value`中的特製化`IDictionary`或`IDictionary<Value>`; 否則為未定義。

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

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)

取代預存的 BCL 控制代碼。

### <a name="syntax"></a>語法

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要複製的配接器。

### <a name="remarks"></a>備註

成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代預存的 BCL 控制代碼，以一份儲存的 BCL 控制代碼*右*。

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

## <a name="reference"></a> collection_adapter::reference (STL/CLR)

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述項目的參考。

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

## <a name="size"></a> collection_adapter::size (STL/CLR)

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 它將不會定義中的特製化`IEnumerable`或`IEnumerable<Value>`。

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

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述的非負數的項目計數。

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

## <a name="swap"></a> collection_adapter::swap (STL/CLR)

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

此成員函式會交換預存的 BCL 控點之間`*this`並*右*。

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

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)

元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

類型是範本參數的同義字*值*，如果出現在特製化; 否則它是同義字`System::Object^`。

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

## <a name="make_collection"></a> make_collection (STL/CLR)

請`range_adapter`迭代器配對。

### <a name="syntax"></a>語法

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>參數

*Iter*<br/>
已包裝的迭代器的類型。

*first*<br/>
要包裝的第一個迭代器。

*最後一個*<br/>
要包裝的第二個迭代器。

### <a name="remarks"></a>備註

此範本函式會傳回 `gcnew range_adapter<Iter>(first, last)`。 您會使用它來建構`range_adapter<Iter>`自一組迭代器物件。

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

## <a name="range_adapter"></a> range_adapter (STL/CLR)

樣板類別，包裝的迭代器用來實作數個基底類別庫 (BCL) 介面的一組。 您可以使用 range_adapter 來操作的 STL/CLR 範圍，如同它是 BCL 集合。

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
與已包裝的迭代器關聯的類型。

### <a name="members"></a>成員

|成員函式|描述|
|---------------------|-----------------|
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|建構的配置器物件。|

|運算子|描述|
|--------------|-----------------|
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|取代預存迭代器配對。|

### <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|逐一查看集合中的項目。|
|<xref:System.Collections.ICollection>|會維護一組項目。|
|<xref:System.Collections.Generic.IEnumerable%601>|逐一查看集合中的具型別項目...|
|<xref:System.Collections.Generic.ICollection%601>|會維護一組具類型的項目。|

### <a name="remarks"></a>備註

Range_adapter 會儲存一組迭代器，依序分隔的項目序列。 物件會實作可讓您逐一查看項目，而在順序中的四個 BCL 介面。 您可以使用此範本類別來操作非常類似 BCL 容器的 STL/CLR 範圍。

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)

取代預存迭代器配對。

### <a name="syntax"></a>語法

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
若要複製的配接器。

### <a name="remarks"></a>備註

成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代預存迭代器配對中的預存迭代器配對的複本*右*。

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

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)

建構的配置器物件。

### <a name="syntax"></a>語法

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>參數

*first*<br/>
要包裝的第一個迭代器。

*最後一個*<br/>
要包裝的第二個迭代器。

*right*<br/>
要複製的物件。

### <a name="remarks"></a>備註

建構函式：

`range_adapter();`

初始化使用預設建構迭代器的預存迭代器配對。

建構函式：

`range_adapter(range_adapter<Iter>% right);`

藉由複製儲存在組初始化預存迭代器配對*右*。

建構函式：

`range_adapter(range_adapter<Iter>^ right);`

藉由複製儲存在組初始化預存迭代器配對`*right`。

建構函式：

`range_adapter(Iter^ first, last);`

初始化預存迭代器配對，其中*第一*並*最後一個*。

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
