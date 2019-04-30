---
title: 編譯器錯誤 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: e11d830c3d662ea424caadeb50df669700f8c78f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406545"
---
# <a name="compiler-error-c3908"></a>編譯器錯誤 C3908

存取層級限制少於 'construct'

屬性存取子方法 （get 或 set） 不能有本身的屬性上指定的存取較不嚴格的存取權。  同樣地，針對事件存取子方法。

如需詳細資訊，請參閱 <<c0> [ 屬性](../../extensions/property-cpp-component-extensions.md)並[事件](../../extensions/event-cpp-component-extensions.md)。

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