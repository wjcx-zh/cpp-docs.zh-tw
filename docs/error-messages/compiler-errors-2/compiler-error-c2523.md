---
title: 編譯器錯誤 C2523 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77f440bf282d6159af3a96bfeb1aa7db8941e87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022795"
---
# <a name="compiler-error-c2523"></a>編譯器錯誤 C2523

' 類別:: ~ 識別碼 ': 解構函式/完成項標記不相符

解構函式的名稱必須是類別名稱加上波狀符號 (`~`)。 建構函式和解構函式是唯一的成員具有相同名稱做為類別。

下列範例會產生 C2523:

```
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```