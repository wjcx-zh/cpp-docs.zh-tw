---
title: 編譯器錯誤 C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 9dfdee155e85bd772ed1d4ce22c525f8a4c79f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458743"
---
# <a name="compiler-error-c3551"></a>編譯器錯誤 C3551

"必須是晚期指定的傳回類型"

如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 在下列範例中， `myFunction` 函式的晚期指定的傳回類型是一個指標，而這個指標指向類型 `int`之四個項目的陣列。

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>另請參閱

[auto](../../cpp/auto-cpp.md)