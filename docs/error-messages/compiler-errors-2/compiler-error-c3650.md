---
title: 編譯器錯誤 C3650 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3650
dev_langs:
- C++
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee7477acc26621a13a1a1d3b4f2d0d0f563c665
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016542"
---
# <a name="compiler-error-c3650"></a>編譯器錯誤 C3650

'interface_method': 不能當成明確覆寫使用，必須是基底類別虛擬成員函式

您嘗試對不是虛擬成員的明確覆寫。

如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。

下列範例會產生 C3650:

```
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```