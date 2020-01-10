---
title: 編譯器錯誤 C2345
ms.date: 11/04/2016
f1_keywords:
- C2345
helpviewer_keywords:
- C2345
ms.assetid: e1cc88b0-0223-4d07-975b-fa99956a82bd
ms.openlocfilehash: 85d9e312bafe0cf6c9390f7484281e1aefb22aab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760019"
---
# <a name="compiler-error-c2345"></a>編譯器錯誤 C2345

align(value): 使用不合法的 align 值

您已將值傳遞給超出容許範圍的 [align](../../cpp/align-cpp.md) 關鍵字。

下列程式碼會產生 C2345。

```cpp
// C2345.cpp
// compile with: /c
__declspec(align(0)) int a;   // C2345
__declspec(align(1)) int a;   // OK
```
