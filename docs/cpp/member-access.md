---
title: 成員存取
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179415"
---
# <a name="member-access"></a>成員存取

類別成員存取可以藉由多載成員存取運算子（ **->** ）來加以控制。 在這種用法中，這個運算子會視為一元運算子，而多載運算子函式必須是類別成員函式。 因此，這類函式的宣告如下：

## <a name="syntax"></a>語法

```
class-type *operator->()
```

## <a name="remarks"></a>備註

其中，*類別類型*是此運算子所屬的類別名稱。 成員存取運算子函式必須是非靜態成員函式。

這個運算子 (通常會搭配指標取值運算子) 會用來實作「智慧型指標」，這類指標會在取值或計數用法之前驗證指標。

**.** 成員存取運算子無法多載。

## <a name="see-also"></a>另請參閱

[運算子多載](../cpp/operator-overloading.md)
