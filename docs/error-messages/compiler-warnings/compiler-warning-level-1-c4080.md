---
title: 編譯器警告 (層級 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: a91963d524300c8768768a8a4615b1ab27e033e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599793"
---
# <a name="compiler-warning-level-1-c4080"></a>編譯器警告 (層級 1) C4080

必須是區段名稱的識別項，但卻找到 'symbol'

[#pragma alloc_text](../../preprocessor/alloc-text.md) 中的區段名稱必須是字串或識別項。 如果找不到有效的識別項，則編譯器會忽略 pragma。

下列範例會產生 C4080：

```
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```