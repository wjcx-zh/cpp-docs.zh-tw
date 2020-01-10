---
title: 編譯器錯誤 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749031"
---
# <a name="compiler-error-c3908"></a>編譯器錯誤 C3908

存取層級比 ' 建造 ' 的限制低

屬性存取子方法（get 或 set）不能有比在屬性本身上指定的存取限制更少的存取權。  同樣地，針對事件存取子方法。

如需詳細資訊，請參閱[屬性](../../extensions/property-cpp-component-extensions.md)和[事件](../../extensions/event-cpp-component-extensions.md)。

下列範例會產生 C3908：

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```
