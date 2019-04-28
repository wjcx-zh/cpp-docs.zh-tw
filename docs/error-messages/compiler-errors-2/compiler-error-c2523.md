---
title: 編譯器錯誤 C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 88a55a469fb8bc08d2ae73209c2e98a99dbc1df0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282192"
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