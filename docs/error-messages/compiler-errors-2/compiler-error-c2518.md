---
title: 編譯器錯誤 C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 894167fce43147b98af6603cba3102e5714b850e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746483"
---
# <a name="compiler-error-c2518"></a>編譯器錯誤 C2518

關鍵字 ' 關鍵字 ' 在基類清單中不合法;忽略

`class` 和 `struct` 的關鍵字不應出現在基類清單中。

下列範例會產生 C2518：

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
