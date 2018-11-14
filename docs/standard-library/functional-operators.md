---
title: '&lt;functional&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: 6fd4e25b3ca7b56e2221cb99b64f7c8e109bf452
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521917"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; 運算子

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a> operator==

測試可呼叫的物件是否是空的。

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>參數

*Fty*<br/>
要包裝的函式類型。

*f*<br/>
函式物件

*npc*<br/>
Null 指標。

### <a name="remarks"></a>備註

運算子同時使用是 `function` 物件之參考的引數以及是 Null 指標常數的引數。 兩者都只有在 `function` 物件為空時，才會傳回 true。

### <a name="example"></a>範例

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a> operator!=

測試可呼叫的物件是否不是空的。

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>參數

*Fty*<br/>
要包裝的函式類型。

*f*<br/>
函式物件

*npc*<br/>
Null 指標。

### <a name="remarks"></a>備註

運算子同時使用是 `function` 物件之參考的引數以及是 Null 指標常數的引數。 兩者都只有在 `function` 物件不是空的時，才會傳回 true。

### <a name="example"></a>範例

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="see-also"></a>另請參閱

[\<functional>](../standard-library/functional.md)<br/>
