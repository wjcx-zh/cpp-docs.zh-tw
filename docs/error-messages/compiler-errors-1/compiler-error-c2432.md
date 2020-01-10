---
title: 編譯器錯誤 C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744507"
---
# <a name="compiler-error-c2432"></a>編譯器錯誤 C2432

' identifier ' 中的16位資料參考不合法

16位暫存器會用來做為索引或基底暫存器。 編譯器不支援參考16位資料。 編譯32位程式碼時，不能使用16位暫存器做為索引或基底暫存器。

下列範例會產生 C2432：

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
