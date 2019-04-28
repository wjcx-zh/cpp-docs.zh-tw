---
title: 編譯器錯誤 C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353193"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555

'class1::function1': 覆寫虛擬函式傳回類型不同，而且不是從 'class2::function2' 的 covariant

虛擬函式和衍生的覆寫函式具有相同的參數清單，但不同的傳回型別。 在衍生類別中的覆寫函式不能在只能由其傳回類型的基底類別中的虛擬函式不同。

若要解決這個錯誤，請呼叫虛擬函式之後轉換傳回的值。

如果您使用 /clr 編譯時，可能也會看到此錯誤。   例如，視覺效果C++相當於下列C#宣告：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

是

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

下列範例會產生 C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```