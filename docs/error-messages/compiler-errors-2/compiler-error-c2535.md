---
title: 編譯器錯誤 C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344712"
---
# <a name="compiler-error-c2535"></a>編譯器錯誤 C2535

'identifier': 已經定義或宣告的成員函式

此錯誤可能被因使用一個以上的定義或宣告的多載的函式中相同的型式參數清單。

如果您因為 Dispose 函式而接到 c2535 錯誤訊息，請參閱[解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)如需詳細資訊。

下列範例會產生 C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```