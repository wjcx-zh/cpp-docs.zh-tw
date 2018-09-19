---
title: 編譯器錯誤 C3908 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7591b8ab5f8495b6af866e23e7a169b0f9cd29a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047313"
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