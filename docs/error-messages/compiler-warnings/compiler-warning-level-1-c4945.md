---
title: 編譯器警告 (層級 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384162"
---
# <a name="compiler-warning-level-1-c4945"></a>編譯器警告 (層級 1) C4945

'symbol': 無法匯入從 'assembly2' 的符號: 'symbol' 已從另一個組件 'assembly1' 匯入

從參考的組件匯入符號，但該符號已經匯入從另一個參考的組件。 請勿參考其中一個組件，或變更其中一個組件中的符號名稱。

下列範例會產生 C4945。

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然後，

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然後，

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```