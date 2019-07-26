---
title: add_cv 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 0cc63558ea392976bd6a3c5a43735c592e4606b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456599"
---
# <a name="addcv-class"></a>add_cv 類別

從類型建立**const volatile**類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>參數

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

`add_cv<T>`已修改類型的實例`type`具有相當於[add_volatile](../standard-library/add-volatile-class.md)和[add_const](../standard-library/add-const-class.md)所修改之*t*的成員**typedef** , 除非*t*已經有 cv 限定詞、參考, 或為函數.

`add_cv_t<T>` 協助程式類型是存取 `add_cv<T>` 成員 typedef `type` 的捷徑。

## <a name="example"></a>範例

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[remove_const 類別](../standard-library/remove-const-class.md)\
[remove_volatile 類別](../standard-library/remove-volatile-class.md)
