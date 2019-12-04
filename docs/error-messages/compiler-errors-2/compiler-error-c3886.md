---
title: 編譯器錯誤 C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: 2e7ba0fcc76d723cebb5b82315faf36313b1d7db
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736629"
---
# <a name="compiler-error-c3886"></a>編譯器錯誤 C3886

' var '：常值資料成員必須初始化

[常](../../extensions/literal-cpp-component-extensions.md)值變數在 declaraed 時必須初始化。

下列範例會產生 C3886：

```cpp
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```
