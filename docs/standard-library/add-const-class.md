---
title: add_const 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: c82a3fac8ef95da9e226ca3e2e9122b3c8774cbf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620835"
---
# <a name="add_const-class"></a>add_const 類別

從類型建立常數類型。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>參數

*Ty*\
要修改的類型。

## <a name="remarks"></a>備註

如果*Ty*是參考、函式或 const 限定的類型，*則類型*修飾詞的實例會保留已修改的類型，否則為 `const Ty` 。

## <a name="example"></a>範例

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>規格需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](type-traits.md)\
[remove_const 類別](remove-const-class.md)
