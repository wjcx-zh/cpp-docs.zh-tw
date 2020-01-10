---
title: 編譯器警告（層級1） C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 6a20effcebe1a36fa1356fffefa3a23a0056a0f0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052251"
---
# <a name="compiler-warning-level-1-c4945"></a>編譯器警告（層級1） C4945

' symbol '：無法從 ' assembly2 ' 匯入符號：因為 ' symbol ' 已從另一個元件 ' assembly1 ' 匯入

符號已從參考的元件匯入，但該符號已從另一個參考的元件匯入。 請不要參考其中一個元件，或在其中一個元件中取得已變更的符號名稱。

下列範例會產生 C4945。

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然後

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然後

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```