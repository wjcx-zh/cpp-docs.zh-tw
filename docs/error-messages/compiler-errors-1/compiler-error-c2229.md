---
title: 編譯器錯誤 C2229 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2229
dev_langs:
- C++
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b235b5fae84ba605ecec5419f9334ccfa0a4be6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035587"
---
# <a name="compiler-error-c2229"></a>編譯器錯誤 C2229

類型 'identifier' 有不合法的大小為零的陣列

結構或位元欄位成員包含不是最後一個成員的大小為零的陣列。

因為您可以為零大小的陣列做為結構的最後一個成員，您必須指定其大小，當您配置結構。

如果為零大小的陣列不是結構的最後一個成員，編譯器就無法計算其餘欄位的位移。

下列範例會產生 C2229:

```
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```