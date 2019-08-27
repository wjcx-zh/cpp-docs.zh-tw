---
title: '&lt;functional&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243765"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; 運算子

## <a name="op_eq_eq"></a> 運算子 = =

測試可呼叫的物件是否是空的。

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>參數

*Fty*\
要包裝的函式類型。

*F*\
函式物件

*npc*\
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

## <a name="op_neq"></a> 運算子 ！ =

測試可呼叫的物件是否不是空的。

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>參數

*Fty*\
要包裝的函式類型。

*F*\
函式物件

*npc*\
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
