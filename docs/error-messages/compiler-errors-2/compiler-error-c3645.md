---
title: 編譯器錯誤 C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: 504b13aeb37fae0c350ef88798fefaec6f26c8e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757822"
---
# <a name="compiler-error-c3645"></a>編譯器錯誤 C3645

' function '： __clrcall 不能用在編譯為機器碼的函式上

函式中有一些關鍵字會導致函式編譯為原生。

## <a name="example"></a>範例

下列範例會產生 C3645。

```cpp
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```
