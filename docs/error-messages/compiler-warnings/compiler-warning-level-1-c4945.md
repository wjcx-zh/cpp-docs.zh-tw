---
title: 編譯器警告 (層級 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 15a78877dbe70a7f95674092984546219e6a1c78
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199121"
---
# <a name="compiler-warning-level-1-c4945"></a>編譯器警告 (層級 1) C4945

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
