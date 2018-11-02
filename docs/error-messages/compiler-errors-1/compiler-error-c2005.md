---
title: 編譯器錯誤 C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: 49d0375d5733410d728797d2a881075377b33ba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535534"
---
# <a name="compiler-error-c2005"></a>編譯器錯誤 C2005

\#列必須有行號，找到 'token'

`#line`指示詞後面必須接著行號。

下列範例會產生 C2005:

```
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

可能的解決方式：

```
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```