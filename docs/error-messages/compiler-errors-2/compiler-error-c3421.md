---
title: 編譯器錯誤 C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 399224a3d091a26066a03df0c77511997ae2403c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182416"
---
# <a name="compiler-error-c3421"></a>編譯器錯誤 C3421

'type' : 您不能呼叫這個類別的完成項，因為它無法存取，或者不存在

完成項是隱含私用的，因此無法從其封入類型外部呼叫。

如需詳細資訊，請參閱[解構函式和完成項中如何：定義和使用類別和結構 (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>範例

下列範例會產生 C3421。

```
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```