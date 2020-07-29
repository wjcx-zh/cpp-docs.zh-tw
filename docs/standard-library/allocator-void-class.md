---
title: allocator&lt;void&gt; 類別
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204926"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 類別

類別樣板配置器至類型的特製化 **`void`** ，定義在此內容中有意義的類型。

## <a name="syntax"></a>語法

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>備註

類別明確特製化[類型的類別](allocator-class.md)樣板配置器 **`void`** 。 其「函式」和「指派運算子」的行為與類別樣板相同，但它只會定義下列類型：

- [const_pointer](allocator-class.md#const_pointer)。

- [指標](allocator-class.md#pointer)。

- [value_type](allocator-class.md#value_type)。

- 重新系[結，這](allocator-class.md#rebind)是一個嵌套類別範本。
