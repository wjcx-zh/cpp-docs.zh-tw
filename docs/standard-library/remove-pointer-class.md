---
title: remove_pointer 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_pointer
helpviewer_keywords:
- remove_pointer class
- remove_pointer
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
ms.openlocfilehash: 786a1cba5fc35014e33e3e19245271adefec1372
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451245"
---
# <a name="removepointer-class"></a>remove_pointer 類別

從類型指標建立類型

## <a name="syntax"></a>語法

```cpp
template <class T>
struct remove_pointer;

template <class T>
using remove_pointer_t = typename remove_pointer<T>::type;
```

### <a name="parameters"></a>參數

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

的`remove_pointer<T>`實例會保存已修改的類型, 當`T1` *T*的`T1*`格式為、 `T1* volatile` `T1* const`、或`T1* const volatile`, 則為, 否則為*t*。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_pointer_t<int *> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_pointer_t<int *> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_pointer_t<int *> == int
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[add_pointer 類別](../standard-library/add-pointer-class.md)
