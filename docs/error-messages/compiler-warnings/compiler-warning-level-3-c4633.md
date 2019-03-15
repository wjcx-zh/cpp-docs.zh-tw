---
title: 編譯器警告 (層級 3) C4633
ms.date: 11/04/2016
f1_keywords:
- C4633
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
ms.openlocfilehash: 039489a804bb5d2bd17186b22bcfb8bea644c377
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812144"
---
# <a name="compiler-warning-level-3-c4633"></a>編譯器警告 (層級 3) C4633

XML 文件註解目標： 錯誤： 原因

將名稱傳遞給[ \<param >](../../build/reference/param-visual-cpp.md)編譯器找不到標記。

下列範例會產生 C4633:

```
// C4633.cpp
// compile with: /clr /doc /LD /W3

/// Text for class MyClass.
public ref class MyClass {
   // C4633 remove line for Int3
   /// <param name="Int1">Used to indicate status.</param>
   /// <param name="Int3">Used to indicate status.</param>
   void MyMethod(int Int1) {
      Int1 = 0;
      Int1++;
   }
};
```