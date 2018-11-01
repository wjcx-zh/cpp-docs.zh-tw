---
title: 編譯器錯誤 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537419"
---
# <a name="compiler-error-c2272"></a>編譯器錯誤 C2272

'function': 靜態成員函式不允許修飾詞

A`static`成員函式以規範來宣告記憶體模型，例如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)，和上不允許這類的修飾詞`static`成員函式。

下列範例會產生 C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```