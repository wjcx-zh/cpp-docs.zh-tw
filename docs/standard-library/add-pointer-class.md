---
title: add_pointer 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 759867a542aa128755ba31e090984eb5b3fe6963
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456551"
---
# <a name="addpointer-class"></a>add_pointer 類別

從指定的類型建立類型指標。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>參數

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

成員**typedef** `type` 的名稱與類型相同。`remove_reference<T>::type*` 別名`add_pointer_t`是存取成員**typedef** `type`的快捷方式。

由於不能從參考建立指標，因此在建立類型指標之前，`add_pointer` 會從指定的類型移除參考 (如果有的話)。 因此，您可以使用類型與 `add_pointer`，而不用擔心類型是否為參考。

## <a name="example"></a>範例

下列範例會示範，類型的 `add_pointer` 與該類型的指標相同。

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[remove_pointer 類別](../standard-library/remove-pointer-class.md)
