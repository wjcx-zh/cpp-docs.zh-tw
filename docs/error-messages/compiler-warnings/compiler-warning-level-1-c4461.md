---
title: 編譯器警告 (層級 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 819c433a58c6b0c3a3958b483dc1d1a08bde58c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186747"
---
# <a name="compiler-warning-level-1-c4461"></a>編譯器警告 (層級 1) C4461

' type '：這個類別具有完成項 ' finalizer '，但沒有任何析構函式 ' dtor '

類型中的完成項存在意味著要刪除的資源。 除非已從型別的「析構函式」明確呼叫完成項，否則當您的物件超出範圍時，common language runtime 會決定執行完成項的時機。

如果您在型別中定義了一個析構函式，並從析構函式明確地呼叫完成項，您可以確定執行完成項。

如需詳細資訊，請參閱[析構函數和](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)完成項。

## <a name="example"></a>範例

下列範例會產生 C4461。

```cpp
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
