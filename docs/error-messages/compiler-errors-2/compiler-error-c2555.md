---
title: 編譯器錯誤 C2555
description: Visual Studio c + + 編譯器錯誤 C2555 的參考。
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ecac92bc663a6344e9ddafe13c194a92ab944c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207793"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555

> '*class1*：：*function1*'：覆寫虛擬函式傳回類型不同，而且不是 '*class2*：：*function2*' 的協變數

虛擬函式和衍生的覆寫函數具有相同的參數清單，但傳回類型不同。

## <a name="remarks"></a>備註

在 c + + 中，衍生類別中的覆寫函數不能只有基類中虛擬函式的傳回類型不同。

針對某些傳回類型，此規則有例外狀況。 當衍生類別覆寫公用基類時，它可能會傳回衍生類別的指標或參考，而不是基類指標或參考。 這些傳回類型稱為「*協*變數」，因為它們會隨著類型而不同。 此規則例外狀況不允許以協變數的參考指標或指標指向指標類型。

解決錯誤的方法之一，就是傳回與基類相同的型別。 然後，在呼叫虛擬函式之後，轉換傳回值。 另一個也是變更參數清單，使衍生的類別成員函式成為多載，而不是覆寫。

## <a name="examples"></a>範例

如果您使用進行編譯，可能會看到這個錯誤 **`/clr`** 。 例如，c + + 相當於下列 c # 宣告：

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
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

若要修正此問題，請將的傳回類型變更 `Y::func` 為 **`void`** 。
