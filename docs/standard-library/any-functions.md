---
title: '&lt;任何&gt;函式'
ms.date: 04/04/2019
f1_keywords:
- any/std::any_cast
- any/std::make_any
- any/std::swap
ms.openlocfilehash: bb5f8b4411477cfcd33613ee0395227dced784f6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268740"
---
# <a name="ltanygt-functions"></a>&lt;任何&gt;函式

## <a name="any_cast"></a> any_cast

可在任何物件。

```cpp
template<class T>
    T any_cast(const any& operand);
template<class T>
    T any_cast(any& operand);
template<class T>
    T any_cast(any&& operand);
template<class T>
    const T* any_cast(const any* operand) noexcept;
template<class T>
    T* any_cast(any* operand) noexcept;
```

## <a name="make_any"></a> make_any

接受的值，並建立任何物件。

```cpp
template <class T, class... Args>
    any make_any(Args&& ...args);
template <class T, class U, class... Args>
    any make_any(initializer_list<U> il, Args&& ...args);
```

## <a name="swap"></a> 交換

任何交換兩個物件的項目。

```cpp
void swap(any& left, any& right) noexcept;
```

### <a name="parameters"></a>參數

*左邊*\
`any` 類型的物件。

*權限*\
`any` 類型的物件。
