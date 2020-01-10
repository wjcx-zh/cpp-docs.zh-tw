---
title: 編譯器錯誤 C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 1e53a0c08f07bf69378fbb7603f63c596f641355
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758654"
---
# <a name="compiler-error-c2524"></a>編譯器錯誤 C2524

' 析構函數 '：析構函式/完成項必須有 ' void ' 參數清單

析構函式或完成項具有不是[void](../../cpp/void-cpp.md)的參數清單。 不允許其他參數類型。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

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
