---
title: 編譯器錯誤 C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216122"
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