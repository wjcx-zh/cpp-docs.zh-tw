---
title: 編譯器錯誤 C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 30aaf67ac9f912059bb5726681e61feabc1e557d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644115"
---
# <a name="compiler-error-c3665"></a>編譯器錯誤 C3665

'解構函式': 覆寫規範 'keyword' 不允許解構函式/完成項

使用解構函式或完成項不允許的關鍵字。

比方說，解構函式或完成項無法要求新的位置。  如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)並[解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

下列範例會產生 C3665:

```
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```