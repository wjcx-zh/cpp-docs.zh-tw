---
title: 編譯器警告 （層級 1） C4461 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86c12208c6992b97f30bc36ea821ba26148ff751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081389"
---
# <a name="compiler-warning-level-1-c4461"></a>編譯器警告 (層級 1) C4461

'type': 此類別具有完成項 'finalizer'，但沒有解構函式 'dtor'

型別中的完成項的存在表示若要刪除的資源。 除非從類型的解構函式明確地呼叫完成項時，通用語言執行平台決定何時執行完成項，您的物件超出範圍。

如果您在類型中定義的解構函式，並明確地從解構函式呼叫的完成項，您可以確定的方式執行完成項。

如需詳細資訊，請參閱 <<c0> [ 解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>範例

下列範例會產生 C4461。

```
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```