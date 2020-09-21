---
title: 編譯器錯誤 C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 57445fec5ee5bb55ac3d16ee21a0e29eb4b21ed1
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743343"
---
# <a name="compiler-error-c2524"></a>編譯器錯誤 C2524

' 函式 '：「函式」/完成項必須有 ' void ' 參數清單

「函式」或完成項的參數清單不是 [void](../../cpp/void-cpp.md)。 不允許其他參數類型。

## <a name="examples"></a>範例

下列程式碼會重現 C2524。

```cpp
// C2524.cpp
// compile with: /c
class A {
   A() {}
   ~A(int i) {}    // C2524
   // try the following line instead
   // ~A() {}
};
```

下列程式碼會重現 C2524。

```cpp
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```
