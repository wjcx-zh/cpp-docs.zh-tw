---
title: 編譯器錯誤 C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202420"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555

' class1：： function1 '：覆寫虛擬函式傳回類型不同，而且不是 ' class2：： function2 ' 的協變數

虛擬函式和衍生的覆寫函數具有相同的參數清單，但傳回類型不同。 衍生類別中的覆寫函式不能與基類中的虛擬函式（只有其傳回型別）不同。

若要解決這個錯誤，請在呼叫虛擬函式之後，轉換傳回值。

如果您使用/clr 進行編譯，可能也會看到此錯誤   例如，對等的C++視覺效果相當於C#下列宣告：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

是

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

下列範例會產生 C2555：

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
