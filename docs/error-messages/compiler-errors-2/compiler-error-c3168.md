---
title: 編譯器錯誤 C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: 4f09c7e250b4c2b02ba2db582f92d54336bed673
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761786"
---
# <a name="compiler-error-c3168"></a>編譯器錯誤 C3168

' type '：列舉的基礎類型不合法

您為 `enum` 類型指定的基礎類型無效。 基礎類型必須是整數C++類資料類型或對應的 CLR 類型。

下列範例會產生 C3168：

```cpp
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
