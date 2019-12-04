---
title: 編譯器錯誤 C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 9dbb0328aa1810d55f2d974aed822992b53101b5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736655"
---
# <a name="compiler-error-c3883"></a>編譯器錯誤 C3883

' var '： initonly 靜態資料成員必須初始化

以[initonly](../../dotnet/initonly-cpp-cli.md)標記的變數未正確初始化。

下列範例會產生 C3883：

```cpp
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

下列範例示範可能的解決方式：

```cpp
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

下列範例顯示如何在靜態的函式中初始化：

```cpp
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```
