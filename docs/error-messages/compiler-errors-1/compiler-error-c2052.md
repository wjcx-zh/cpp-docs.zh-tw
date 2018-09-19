---
title: 編譯器錯誤 C2052 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2052
dev_langs:
- C++
helpviewer_keywords:
- C2052
ms.assetid: 922ca43b-b64b-4ef7-9611-c7313be3fd79
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b078efbd0d0d99a145bcada6266f8e886e4251a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018675"
---
# <a name="compiler-error-c2052"></a>編譯器錯誤 C2052

'type': case 運算式的類型不合法

Case 運算式必須是整數常數。

下列範例會產生 C2052:

```
// C2052.cpp
int main() {
   int index = 0;
   switch (index) {
      case 1:
         return 24;
      case 1.0:   // C2052
      // try the following line instead
      // case 2:
         return 23;
   }
}
```