---
title: is_same 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_same
dev_langs:
- C++
helpviewer_keywords:
- is_same class
- is_same
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07b886b805eb551831ad2d559b041df0d38c5987
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="issame-class"></a>is_same 類別

測試兩個類型是否相同。

## <a name="syntax"></a>語法

```cpp
template <class Ty1, class Ty2>
struct is_same;
```

### <a name="parameters"></a>參數

`Ty1` 要查詢的第一個類型。

`Ty2` 要查詢的第二個類型。

## <a name="remarks"></a>備註

如果類型 `Ty1` 與 `Ty2` 相同，則類型述詞的執行個體為 true，否則為 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_same.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_same<base, base> == " << std::boolalpha
        << std::is_same<base, base>::value << std::endl;
    std::cout << "is_same<base, derived> == " << std::boolalpha
        << std::is_same<base, derived>::value << std::endl;
    std::cout << "is_same<derived, base> == " << std::boolalpha
        << std::is_same<derived, base>::value << std::endl;
    std::cout << "is_same<int, int> == " << std::boolalpha
        << std::is_same<int, int>::value << std::endl;
    std::cout << "is_same<int, const int> == " << std::boolalpha
        << std::is_same<int, const int>::value << std::endl;

    return (0);
    }

```

```Output
is_same<base, base> == true
is_same<base, derived> == false
is_same<derived, base> == false
is_same<int, int> == true
is_same<int, const int> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_convertible 類別](../standard-library/is-convertible-class.md)<br/>
[is_base_of 類別](../standard-library/is-base-of-class.md)<br/>
