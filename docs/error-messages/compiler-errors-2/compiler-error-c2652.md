---
title: 編譯器錯誤 C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756119"
---
# <a name="compiler-error-c2652"></a>編譯器錯誤 C2652

' identifier '：不合法的複製函數：第一個參數不得為 ' identifier '

複製函式中的第一個參數與定義它的類別、結構或聯集具有相同的類型。 第一個參數可以是類型的參考，而不是類型本身。

下列範例會產生 C2651：

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
