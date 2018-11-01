---
title: 編譯器錯誤 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598009"
---
# <a name="compiler-error-c2467"></a>編譯器錯誤 C2467

匿名 '使用者定義的型別' 的宣告不合法

宣告的巢狀的使用者定義型別。 編譯 c# 原始程式碼使用 ANSI 相容性選項時，這會是錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 啟用。

下列範例會產生 C2467:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```