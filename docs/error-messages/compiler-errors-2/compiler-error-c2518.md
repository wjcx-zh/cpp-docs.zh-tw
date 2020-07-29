---
title: 編譯器錯誤 C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 315edc3124b4cdd425ce9d7581167366d3831512
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214642"
---
# <a name="compiler-error-c2518"></a>編譯器錯誤 C2518

關鍵字 ' 關鍵字 ' 在基類清單中不合法;忽略

關鍵字 **`class`** 和 **`struct`** 不應該出現在基類清單中。

下列範例會產生 C2518：

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
