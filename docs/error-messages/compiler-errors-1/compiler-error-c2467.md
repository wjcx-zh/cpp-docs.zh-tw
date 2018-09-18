---
title: 編譯器錯誤 C2467 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bab320bfdba9fcbd408771b7859a22fc85fa06e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048769"
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