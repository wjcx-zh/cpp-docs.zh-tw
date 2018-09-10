---
title: array 類別 (C++ 標準程式庫)| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
dev_langs:
- C++
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c52a68e87e29aaa827a61e657e04364acf6205b4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318783"
---
# <a name="array-class-c-standard-library"></a>array 類別 (C++ 標準程式庫)

說明的物件可控制長度 `N` 之 `Ty` 類型項目的序列。 序列會儲存成陣列 `Ty`，包含在 `array<Ty, N>` 物件中。

## <a name="syntax"></a>語法

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`Ty`|元素的類型。|
|`N`|元素數。|

## <a name="members"></a>成員

|類型定義|描述|
|-|-|
|[const_iterator](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[const_pointer](#const_pointer)|項目的常數指標類型。|
|[const_reference](#const_reference)|項目的常數參考類型。|
|[const_reverse_iterator](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[difference_type](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[iterator](#iterator)|受控制序列之迭代器的類型。|
|[pointer](#pointer)|項目的指標類型。|
|[reference](#reference)|項目的參考類型。|
|[reverse_iterator](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[size_type](#size_type)|兩個項目之間不帶正負號距離的類型。|
|[value_type](#value_type)|元素的類型。|

|成員函式|描述|
|-|-|
|[array](#array)|建構陣列物件。|
|[assign](#assign)|取代所有項目。|
|[at](#at)|存取指定位置的項目。|
|[back](#back)|存取最後一個項目。|
|[begin](#begin)|指定受控制序列的開頭。|
|[cbegin](#cbegin)|將隨機存取常數迭代器傳回陣列中的第一個項目。|
|[cend](#cend)|傳回隨機存取指向陣列結尾之後一個項目的常數迭代器。|
|[crbegin](#crbegin)|將常數迭代器傳回反向陣列中的第一個項目。|
|[crend](#crend)|將常數迭代器傳回反向陣列的結尾。|
|[data](#data)|取得第一個項目的位址。|
|[empty](#empty)|測試項目是否存在。|
|[end](#end)|指定受控制序列的結尾。|
|[fill](#fill)|取代所有具有指定值的項目。|
|[front](#front)|存取第一個項目。|
|[max_size](#max_size)|計算元素的數目。|
|[rbegin](#rbegin)|指定反向受控制序列的開頭。|
|[rend](#rend)|指定反向受控制序列的結尾。|
|[size](#size)|計算元素的數目。|
|[swap](#swap)|交換兩個容器的內容。|

|運算子|描述|
|-|-|
|[array::operator=](#op_eq)|取代受控制的序列。|
|[array::operator[]](#op_at)|存取指定位置的項目。|

## <a name="remarks"></a>備註

該類型具有預設建構函式 `array()` 與預設指派運算子 `operator=`，且可滿足 `aggregate` 的需求。 因此，`array<Ty, N>` 類型的物件可以使用彙總初始設定式加以初始化。 例如，套用至物件的

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

建立含有四個整數值的物件 `ai`，將前三個項目分別初始化為值 1、 2 和 3，並將第四個項目初始化為 0。

## <a name="requirements"></a>需求

**標頭：**\<array>

**命名空間：** std

## <a name="array"></a> array::array

建構陣列物件。

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

預設建構函式 `array()` 會讓受控制序列處於未初始化狀態 (預設為初始化)。 您使用它來指定未初始化的受控制序列。

複製建構函式 `array(const array& right)` 會使用序列 [*right*`.begin()`, *right*`.end()`) 來初始化受控制序列。 您使用它來指定初始受控制序列，這個初始受控制序列是陣列物件 *right* 所控制序列的複本。

### <a name="example"></a>範例

```cpp
// std__array__array_array.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1(c0);

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="assign"></a> array::assign

在 C++11 中已淘汰，已取代為 [fill](#fill)。 取代所有項目。

```cpp
void assign(const Ty& val);
```

### <a name="parameters"></a>參數

*val*<br/>
要指派的值。

### <a name="remarks"></a>備註

此成員函式會取代所控制的序列`*this`重複`N`值之項目的*val*。

### <a name="example"></a>範例

```cpp
// std__array__array_assign.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1.assign(4);

// display contents " 4 4 4 4"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4 4 4 4
```

## <a name="at"></a> array::at

存取指定位置的項目。

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>參數

*關閉*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員函式會傳回位置的受控制序列的項目參考*關閉*。 如果該位置無效，函式就會擲回類別 `out_of_range` 的物件。

### <a name="example"></a>範例

```cpp
// std__array__array_at.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
    }

```

## <a name="back"></a> array::back

存取最後一個項目。

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的最後一個項目的參考，絕對不能空白。

### <a name="example"></a>範例

```cpp
// std__array__array_back.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="begin"></a> array::begin

指定受控制序列的開頭。

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>備註

成員函式傳回的隨機存取迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)。

### <a name="example"></a>範例

```cpp
// std__array__array_begin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="cbegin"></a> array::cbegin

傳回**const**迭代器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

A **const**隨機存取迭代器指向第一個項目範圍或只是空白範圍結尾之外的位置 (空白範圍， `cbegin() == cend()`)。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮`Container`的可修改 (非**const**) 的任何一種支援的容器`begin()`和`cbegin()`。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a> array::cend

傳回**const**迭代器，定址範圍中最後一個項目之外的位置。

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的隨機存取迭代器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮`Container`的可修改 (非**const**) 的任何一種支援的容器`end()`和`cend()`。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="const_iterator"></a> array::const_iterator

用於受控制序列的常數迭代器類型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

此類型所描述的物件可作為受控制序列的常數隨機存取迭代器。

### <a name="example"></a>範例

```cpp
// std__array__array_const_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::const_iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="const_pointer"></a> array::const_pointer

項目的常數指標類型。

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>備註

此類型所描述的物件可以作為序列之元素的常數指標。

### <a name="example"></a>範例

```cpp
// std__array__array_const_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reference"></a> array::const_reference

項目的常數參考類型。

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可作為受控制序列之元素的常數參考。

### <a name="example"></a>範例

```cpp
// std__array__array_const_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reverse_iterator"></a> array::const_reverse_iterator

用於受控制序列的常數反向迭代器類型。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型所描述的物件可作為受控制序列的常數反向迭代器。

### <a name="example"></a>範例

```cpp
// std__array__array_const_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="crbegin"></a> array::crbegin

將常數迭代器傳回反向陣列中的第一個項目。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

const 反轉隨機存取迭代器，其定址反轉陣列中的第一個項目，或定址未反轉陣列中的最後一個項目。

### <a name="remarks"></a>備註

有 `crbegin` 的傳回值時，無法修改陣列物件。

### <a name="example"></a>範例

```cpp
// array_crbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="crend"></a> array::crend

傳回 const 迭代器，其定址反轉陣列中最後一個元素的下一個位置。

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>傳回值

const 反轉隨機存取迭代器，其定址反轉陣列中最後一個元素的下一個位置 (此位置在未反轉的陣列中優先於第一個元素)。

### <a name="remarks"></a>備註

`crend` 用於反向陣列，就如同 [array::cend](#cend) 用於陣列一樣。

有 `crend` 的傳回值時 (適當遞減)，無法修改陣列物件。

`crend` 可以用來測試反轉迭代器是否已到達其陣列的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// array_crend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a> array::data

取得第一個項目的位址。

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>備註

這些成員函式會傳回受控制序列中第一個元素的位址。

### <a name="example"></a>範例

```cpp
// std__array__array_data.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="difference_type"></a> array::difference_type

兩個項目之間帶正負號距離的類型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>備註

此帶正負號的整數類型所描述的物件可代表受控制序列中任何兩個項目位址之間的差距。 它是 `std::ptrdiff_t` 類型的同義字。

### <a name="example"></a>範例

```cpp
// std__array__array_difference_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
-4
```

## <a name="empty"></a> array::empty

測試項目是否不存在。

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>備註

唯有 `N == 0` 時，成員函式才會傳回 true。

### <a name="example"></a>範例

```cpp
// std__array__array_empty.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

// display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
false
true
```

## <a name="end"></a> array::end

指定受控制序列的結尾。

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>備註

成員函式會傳回指向序列結尾之外的隨機存取迭代器。

### <a name="example"></a>範例

```cpp
// std__array__array_end.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="fill"></a> array::fill

清除陣列，並將指定的項目複製到空陣列。

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|*val*|插入陣列中之項目的值。|

### <a name="remarks"></a>備註

`fill` 會以指定的值取代陣列的每個項目。

### <a name="example"></a>範例

```cpp
// array_fill.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator iter;

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v1.fill(3);
   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="front"></a> array::front

存取第一個項目。

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的第一個項目的參考，絕對不能空白。

### <a name="example"></a>範例

```cpp
// std__array__array_front.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="iterator"></a> array::iterator

受控制序列之迭代器的類型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

此類型說明可作為受控制序列之隨機存取迭代器的物件。

### <a name="example"></a>範例

```cpp
// std__array__array_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3

it2: 0

```

## <a name="max_size"></a> array::max_size

計算元素的數目。

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回 `N`。

### <a name="example"></a>範例

```cpp
// std__array__array_max_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="op_at"></a> array::operator[]

存取指定位置的項目。

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>參數

*關閉*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員函式會傳回位置的受控制序列的項目參考*關閉*。 如果位置不正確，就不會定義行為。

另外還有非成員[取得](array-functions.md#get)函式可用來取得參考之項目的**陣列**。

### <a name="example"></a>範例

```cpp
// std__array__array_operator_sub.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
1 3
```

## <a name="op_eq"></a> array::operator=

取代受控制的序列。

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>參數

*right*<br/>
要複製的容器。

### <a name="remarks"></a>備註

此成員運算子會將指派的每個項目*右*受控制序列的對應項目，然後傳回`*this`。 您使用它來取代受控制的序列中的受控制序列的複本*右*。

### <a name="example"></a>範例

```cpp
// std__array__array_operator_as.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

// display copied contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="pointer"></a> array::pointer

項目的指標類型。

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>備註

此類型所描述的物件可以作為序列之元素的指標。

### <a name="example"></a>範例

```cpp
// std__array__array_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rbegin"></a> array::rbegin

指定反向受控制序列的開頭。

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>備註

成員函式會傳回指向受控制序列結尾之外的反向迭代器。 因此，它會指定反向序列的開頭。

### <a name="example"></a>範例

```cpp
// std__array__array_rbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="reference"></a> array::reference

項目的參考類型。

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之元素的參考。

### <a name="example"></a>範例

```cpp
// std__array__array_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rend"></a> array::rend

指定反向受控制序列的結尾。

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>備註

成員函式傳回的反向迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)。 因此，它會指定反向序列的結尾。

### <a name="example"></a>範例

```cpp
// std__array__array_rend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="reverse_iterator"></a> array::reverse_iterator

受控制序列的反向迭代器類型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

此類型所描述的物件可作為受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// std__array__array_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="size"></a> array::size

計算元素的數目。

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回 `N`。

### <a name="example"></a>範例

```cpp
// std__array__array_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="size_type"></a> array::size_type

兩個元素之間不帶正負號距離的類型。

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>備註

此不帶正負號的整數類型所描述的物件可代表任何受控制序列的長度。 它是 `std::size_t` 類型的同義字。

### <a name="example"></a>範例

```cpp
// std__array__array_size_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="swap"></a> array::swap

將這個陣列的內容與另一個陣列交換。

```cpp
void swap(array& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要與之交換內容的陣列。

### <a name="remarks"></a>備註

此成員函式會交換之間受控制的序列`*this`並*右*。 它會執行多個元素指派，以及與 `N` 成正比的建構函式呼叫。

另外還有非成員[交換](array-functions.md#swap)函式可用來交換兩個**陣列**執行個體。

### <a name="example"></a>範例

```cpp
// std__array__array_swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};
    c0.swap(c1);

// display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

// display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="value_type"></a> array::value_type

元素的類型。

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Ty`的同義字。

### <a name="example"></a>範例

```cpp
// std__array__array_value_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        {
        Myarray::value_type val = *it;
        std::cout << " " << val;
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>另請參閱

[\<array>](../standard-library/array.md)<br/>
