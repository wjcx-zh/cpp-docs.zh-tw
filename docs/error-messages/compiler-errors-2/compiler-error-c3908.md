---
title: 編譯器錯誤 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 84b21f20cbc8203a9cd70e487738c34c6ad3a89b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598922"
---
# <a name="compiler-error-c3908"></a>編譯器錯誤 C3908

存取層級限制少於 'construct'

屬性存取子方法 （get 或 set） 不能有本身的屬性上指定的存取較不嚴格的存取權。  同樣地，針對事件存取子方法。

如需詳細資訊，請參閱 <<c0> [ 屬性](../../windows/property-cpp-component-extensions.md)並[事件](../../windows/event-cpp-component-extensions.md)。

下列範例會產生 C3908:

```
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