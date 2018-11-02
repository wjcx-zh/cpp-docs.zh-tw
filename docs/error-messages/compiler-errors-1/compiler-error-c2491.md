---
title: 編譯器錯誤 C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 3b48bebde6d7baedea73ed181cd4ea33adc44a69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563120"
---
# <a name="compiler-error-c2491"></a>編譯器錯誤 C2491

'identifier': 不允許定義 dllimport 函式

資料、靜態資料成員和函式可以宣告為 `dllimport`，但不可定義為 `dllimport`。

若要修正這個問題，請從函式定義移除 `__declspec(dllimport)` 規範。

下列範例會產生 C2491：

```
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```