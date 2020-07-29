---
title: 編譯器錯誤 C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: a40a79c48b0f437271063e555593464f55fe9837
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212588"
---
# <a name="compiler-error-c3168"></a>編譯器錯誤 C3168

' type '：列舉的基礎類型不合法

您為類型指定的基礎類型無效 **`enum`** 。 基礎類型必須是整數 c + + 類型或對應的 CLR 類型。

下列範例會產生 C3168：

```cpp
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
