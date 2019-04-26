---
title: 編譯器錯誤 C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166837"
---
# <a name="compiler-error-c2432"></a>編譯器錯誤 C2432

'identifier' 中的 16 位元資料的參考不合法

16 位元暫存器做為索引或基底暫存器。 編譯器不支援參考 16 位元資料。 16 位元暫存器不能用作基底或索引暫存器的 32 位元程式碼進行編譯時。

下列範例會產生 C2432:

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```