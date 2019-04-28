---
title: 編譯器錯誤 C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 11d5a0a86ba399e28a641fa490f19be020db2d9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301431"
---
# <a name="compiler-error-c2087"></a>編譯器錯誤 C2087

'identifier': 遺漏註標

具有多個註標的陣列定義遺漏高於其中一個維度的下標值。

下列範例會產生 C2087:

```
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

可能的解決方式：

```
// C2087b.cpp
int main() {
   char b[4][5];
}
```