---
title: add_pointer 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 102984fc0384499f5aa2538a0f8d858578096551
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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

*T*来修改的類型。

## <a name="remarks"></a>備註

成員 typedef `type` 名稱與 `remove_reference<T>::type*` 的類型相同。 `add_pointer_t` 別名是存取成員 typedef `type` 的捷徑。

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

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer 類別](../standard-library/remove-pointer-class.md)<br/>
