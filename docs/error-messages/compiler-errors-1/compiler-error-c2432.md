---
title: 編譯器錯誤 C2432 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca8c2c62415b6ec3c29c820a23677a87a2695c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055906"
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