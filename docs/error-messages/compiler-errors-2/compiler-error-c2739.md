---
title: 編譯器錯誤 C2739 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2739
dev_langs:
- C++
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4e6c757823caa25bd9df890dce35035642e5212
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046663"
---
# <a name="compiler-error-c2739"></a>編譯器錯誤 C2739

'number'：明確的 Managed 或 WinRT 陣列維度必須是介於 1 到 32 之間

陣列維度不是介於 1 到 32 之間。

下列範例會產生 C2739，並示範如何修正此問題：

```
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```