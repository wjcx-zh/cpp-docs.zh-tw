---
title: 編譯器錯誤 C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735745"
---
# <a name="compiler-error-c2086"></a>編譯器錯誤 C2086

' identifier '：重複定義

識別碼定義了一次以上，或後續的宣告與上一個宣告不同。

C2086 也可以是參考C#元件之累加式建築物的結果。 重建C#元件以解決此錯誤。

下列範例會產生 C2086：

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
