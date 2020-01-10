---
title: 編譯器錯誤 C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 7ee7fb6e66ca9d5e09ad0eb445262c5f87d2060e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757068"
---
# <a name="compiler-error-c2491"></a>編譯器錯誤 C2491

'identifier': 不允許定義 dllimport 函式

資料、靜態資料成員和函式可以宣告為 `dllimport`，但不可定義為 `dllimport`。

若要修正這個問題，請從函式定義移除 `__declspec(dllimport)` 規範。

下列範例會產生 C2491：

```cpp
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```
