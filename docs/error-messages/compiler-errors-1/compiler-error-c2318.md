---
title: 編譯器錯誤 C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: a68a333c9cb817a653597acb011dfbb9291c4d0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350578"
---
# <a name="compiler-error-c2318"></a>編譯器錯誤 C2318

沒有和 catch 處理常式關聯的 try 區塊

已定義 `catch` 處理常式，但它前面沒有 `try` 區塊。

下列範例會產生 C2318：

```
// C2318.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   // no try block
   catch( int ) {}   // C2318
}
```

可能的解決方式：

```
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```