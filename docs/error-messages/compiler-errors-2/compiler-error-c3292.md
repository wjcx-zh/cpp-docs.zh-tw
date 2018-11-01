---
title: 編譯器錯誤 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 7c59932a79534a365a20fcad25583f7addc0d624
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609598"
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292

無法重新開啟 cli 命名空間

無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱 < [Platform、 default 和 cli 命名空間](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3292：

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```