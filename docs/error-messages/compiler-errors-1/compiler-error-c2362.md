---
title: 編譯器錯誤 C2362 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f78b850f95614255fed372570742a0f88a9e30e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035977"
---
# <a name="compiler-error-c2362"></a>編譯器錯誤 C2362

'identifier' 的初始化會略過由 'goto label'

進行編譯時[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳至標籤導致無法進行初始化的識別項。

除非宣告括在不輸入，區塊中，您無法跳過具有初始設定式的宣告，或已初始化的變數。

下列範例會產生 C2326：

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解決方式：

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```