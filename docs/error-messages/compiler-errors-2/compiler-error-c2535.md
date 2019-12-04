---
title: 編譯器錯誤 C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: f5cecd847837214f6392bead624e5377cef4833f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758641"
---
# <a name="compiler-error-c2535"></a>編譯器錯誤 C2535

' identifier '：已定義或宣告成員函式

這個錯誤可能是因為在多載函式的一個定義或宣告中使用相同的型式參數清單所造成。

如果您因為 Dispose 函數而取得 C2535，請參閱[析構](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)函式和完成項以取得詳細資訊。

下列範例會產生 C2535：

```cpp
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```
