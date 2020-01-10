---
title: 編譯器錯誤 C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 23433dccd7fc4f86c2e848359ac50c796fcccab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746795"
---
# <a name="compiler-error-c2507"></a>編譯器錯誤 C2507

' identifier '：基類上有太多的虛擬修飾詞

類別或結構宣告為 `virtual` 一次以上。 基類清單中的每個類別都只能出現一個 `virtual` 修飾詞。

下列範例會產生 C2507：

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
