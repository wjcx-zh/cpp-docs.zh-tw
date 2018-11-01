---
title: 編譯器錯誤 C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 369aa5f21c072472808ffba06c3bc5c5e608ac22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640111"
---
# <a name="compiler-error-c2524"></a>編譯器錯誤 C2524

'解構函式': 解構函式/完成項必須擁有 'void' 參數清單

解構函式或完成項必須不是參數清單[void](../../cpp/void-cpp.md)。 不允許其他參數類型。

## <a name="example"></a>範例

下列程式碼會重現 C2524。

```
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

```
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```