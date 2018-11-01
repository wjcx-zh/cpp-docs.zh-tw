---
title: 編譯器錯誤 C2345
ms.date: 11/04/2016
f1_keywords:
- C2345
helpviewer_keywords:
- C2345
ms.assetid: e1cc88b0-0223-4d07-975b-fa99956a82bd
ms.openlocfilehash: ceb2a835ca94399f27640628105afcde986af1b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479101"
---
# <a name="compiler-error-c2345"></a>編譯器錯誤 C2345

align(value): 使用不合法的 align 值

您已將值傳遞給超出容許範圍的 [align](../../cpp/align-cpp.md) 關鍵字。

下列程式碼會產生 C2345。

```
// C2345.cpp
// compile with: /c
__declspec(align(0)) int a;   // C2345
__declspec(align(1)) int a;   // OK
```