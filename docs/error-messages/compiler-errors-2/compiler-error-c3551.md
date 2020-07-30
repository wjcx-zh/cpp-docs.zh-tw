---
title: 編譯器錯誤 C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 1555817de6e50ea27a021718c8b094efeaebacde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230840"
---
# <a name="compiler-error-c3551"></a>編譯器錯誤 C3551

"必須是晚期指定的傳回類型"

如果您使用關鍵字做為函式 **`auto`** 之傳回型別的預留位置，則必須提供晚期指定的傳回型別。 在下列範例中，函式的晚期指定傳回類型 `myFunction` 是類型的四個元素之陣列的指標 **`int`** 。

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>另請參閱

[自動](../../cpp/auto-cpp.md)
