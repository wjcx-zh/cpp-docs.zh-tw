---
title: 編譯器錯誤 C2075
ms.date: 11/04/2016
f1_keywords:
- C2075
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
ms.openlocfilehash: d53ef6f34b061a04f2c136b4e349d4951529b94b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303173"
---
# <a name="compiler-error-c2075"></a>編譯器錯誤 C2075

'identifier': 陣列初始化需要使用大括號

指定的陣列初始設定式未以大括號括住。

下列範例會產生 C2075：

```
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

可能的解決方式：

```
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```