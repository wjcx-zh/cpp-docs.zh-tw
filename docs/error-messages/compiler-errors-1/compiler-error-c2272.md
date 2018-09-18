---
title: 編譯器錯誤 C2272 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2272
dev_langs:
- C++
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e17765ee0acbf20d76e631bf7fccfb3413c5dc1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040306"
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