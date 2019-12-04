---
title: 編譯器錯誤 C2010
ms.date: 11/04/2016
f1_keywords:
- C2010
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
ms.openlocfilehash: 7341c77ecf2863431fa3e5c0a454077c89601b6b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752427"
---
# <a name="compiler-error-c2010"></a>編譯器錯誤 C2010

' character '：宏型式參數清單中有非預期的

在巨集定義的型式參數清單中不正確地使用了該字元。 請移除字元以解決錯誤。

下列範例會產生 C2010：

```cpp
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```
