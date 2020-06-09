---
title: allocator&lt;void&gt; 類別
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: af29c70dca56b1e68eef3614357269c587a77ec9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623671"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 類別

類別樣板配置器對類型**void**的特製化，定義在此內容中有意義的類型。

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

類別明確特製化型別[為](allocator-class.md) **void**的類別樣板配置器。 其「函式」和「指派運算子」的行為與類別樣板相同，但它只會定義下列類型：

- [const_pointer](allocator-class.md#const_pointer)。

- [指標](allocator-class.md#pointer)。

- [value_type](allocator-class.md#value_type)。

- 重新系[結，這](allocator-class.md#rebind)是一個嵌套類別範本。
