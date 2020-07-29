---
title: '&lt;memory&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: 15762e4853cfd018c7cff997a3ed9ba7d86b3c2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233050"
---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt; 運算子

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試物件是否不相等。

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要測試是否不相等的物件之一。

*再*\
要測試是否不相等的物件之一。

*Ty1*\
左側共用指標所控制的類型。

*Ty2*\
右側共用指標所控制的類型。

### <a name="return-value"></a>傳回值

**`true`** 如果物件不相等，則為，**`false`** 如果物件相等則為。

### <a name="remarks"></a>備註

第一個範本運算子會傳回 false。 (所有的預設配置器相等)。

第二個和第三個範本運算子會傳回 `!(left == right)`。

### <a name="example"></a>範例

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>範例

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試物件是否相等。

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要測試是否相等的其中一個物件。

*再*\
要測試是否相等的其中一個物件。

*Ty1*\
左側共用指標所控制的類型。

*Ty2*\
右側共用指標所控制的類型。

### <a name="return-value"></a>傳回值

**`true`** 如果物件相等，則為， **`false`** 如果物件不相等則為。

### <a name="remarks"></a>備註

第一個範本運算子會傳回 true。 (所有的預設配置器相等)。

第二個和第三個範本運算子會傳回 `left.get() ==  right.get()`。

### <a name="example"></a>範例

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>範例

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試一個物件是否大於或等於第二個物件。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的其中一個物件。

*再*\
要比較的其中一個物件。

*Ty1*\
左側共用指標所控制的類型。

*Ty2*\
右側共用指標所控制的類型。

### <a name="remarks"></a>備註

此範本運算子會傳回 `left.get() >= right.get()`。

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試一個物件是否小於第二個物件。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的其中一個物件。

*再*\
要比較的其中一個物件。

*Ty1*\
左側指標所控制的類型。

*Ty2*\
右側指標所控制的類型。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試一個物件是否小於或等於第二個物件。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的其中一個物件。

*再*\
要比較的其中一個物件。

*Ty1*\
左側共用指標所控制的類型。

*Ty2*\
右側共用指標所控制的類型。

### <a name="remarks"></a>備註

這些範本運算子會傳回 `left.get() <= right.get()`。

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試一個物件是否大於第二個物件。

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的其中一個物件。

*再*\
要比較的其中一個物件。

*Ty1*\
左側共用指標所控制的類型。

*Ty2*\
右側共用指標所控制的類型。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>操作&lt;&lt;

將共用指標寫入資料流中。

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>參數

*Elem*\
資料流元素的類型。

*Tr*\
資料流元素特性的類型。

*Ty*\
共用指標所控制的類型。

*脫銷*\
輸出資料流。

*行距*\
共用指標。

### <a name="remarks"></a>備註

此範本函式會傳回 `out << sp.get()`。

### <a name="example"></a>範例

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```
