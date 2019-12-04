---
title: 編譯器錯誤 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 566c92a5dc24c28b334653c6b5507b0bd9330992
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760123"
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292

無法重新開啟 cli 命名空間

無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱[平台、預設與 cli 命名空間](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3292：

```cpp
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```
