---
title: 編譯器錯誤 C2086 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2086
dev_langs:
- C++
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e0d8b105d58b0585bc31b8d340d3d7ba5fb29e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029841"
---
# <a name="compiler-error-c2086"></a>編譯器錯誤 C2086

'identifier': 重複定義

識別項定義了一次以上，或在後續的宣告不同於前一個。

C2086 也可以是累加建置參考的 C# 組件的結果。 重新建置 C# 組件來解決這個錯誤。

下列範例會產生 C2086:

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```