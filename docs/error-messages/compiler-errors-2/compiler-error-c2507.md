---
title: 編譯器錯誤 C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 944eaeadb038e6466d65859f72900db164cfe34d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221155"
---
# <a name="compiler-error-c2507"></a>編譯器錯誤 C2507

' identifier '：基類上有太多的虛擬修飾詞

類別或結構宣告為多次 **`virtual`** 。 **`virtual`** 基類清單中的每個類別都只能出現一個修飾詞。

下列範例會產生 C2507：

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
