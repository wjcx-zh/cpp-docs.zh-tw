---
title: remove_cv 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_cv
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
ms.openlocfilehash: dbe21d8e9f0ed0dc7c72a19584f24ee1bce0803c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451331"
---
# <a name="removecv-class"></a>remove_cv 類別

從類型建立非 const/volatile 類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct remove_cv;

template <class T>
using remove_cv_t = typename remove_cv<T>::type;
```

### <a name="parameters"></a>參數

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

的`remove_cv<T>`實例會保存已修改的類型, 當`T1` *T*的格式`const T1`為、 `volatile T1`或`const volatile T1`, 則為, 否則為*t*。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_cv_t<const volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_cv_t<const volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_cv_t<const volatile int> == int
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[remove_const 類別](../standard-library/remove-const-class.md)\
[remove_volatile 類別](../standard-library/remove-volatile-class.md)
