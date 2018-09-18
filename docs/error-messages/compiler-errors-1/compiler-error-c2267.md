---
title: 編譯器錯誤 C2267 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2267
dev_langs:
- C++
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 080f6ebfda8dbdaa1f0bf70faa3b6d5c7545d66e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035262"
---
# <a name="compiler-error-c2267"></a>編譯器錯誤 C2267

'function': 具有區塊範圍的靜態函式不合法

區域函式宣告`static`。 靜態函式必須具有全域範圍。

下列範例會產生 C2267:

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```