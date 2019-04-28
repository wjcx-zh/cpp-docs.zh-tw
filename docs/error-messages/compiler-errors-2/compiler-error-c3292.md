---
title: 編譯器錯誤 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: a68d3e922532480063fe4c294e40f453885743e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222626"
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292

無法重新開啟 cli 命名空間

無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱 < [Platform、 default 和 cli 命名空間](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3292：

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```