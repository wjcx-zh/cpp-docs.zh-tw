---
title: 編譯器錯誤 C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 4b0c019b2425b314f5b3503db41042d917283aa8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758173"
---
# <a name="compiler-error-c3665"></a>編譯器錯誤 C3665

' 析構函數 '：在析構函式/完成項上不允許有覆寫規範 ' 關鍵字 '

在析構函數或完成項上使用了不允許的關鍵字。

例如，無法在析構函式或完成項上要求新的位置。  如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)和析構函式[和](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)完成項。

下列範例會產生 C3665：

```cpp
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
