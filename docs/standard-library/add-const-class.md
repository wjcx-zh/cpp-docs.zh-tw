---
title: add_const 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_const
dev_langs:
- C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46d0d52f53a45b53c8634a40c56feb167793e565
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102832"
---
# <a name="addconst-class"></a>add_const 類別

從類型建立常數類型。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要修改的類型。

## <a name="remarks"></a>備註

類型修飾詞的執行個體保留修改的類型所*Ty*如果*Ty*是參考、 函式或 const 限定的類型，否則`const Ty`。

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

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const 類別](../standard-library/remove-const-class.md)<br/>
