---
title: 編譯器錯誤 C3273
ms.date: 11/04/2016
f1_keywords:
- C3273
helpviewer_keywords:
- C3273
ms.assetid: 1d2ce9d9-222b-4cab-94e2-d2c1a9f5ebe0
ms.openlocfilehash: 5ab0d4f51ef893d263e219a3915bce9be52ffec0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753831"
---
# <a name="compiler-error-c3273"></a>編譯器錯誤 C3273

__finally 不能用在 Unmanaged 程式碼的例外狀況區塊上。

下列範例會產生 C3273：

```cpp
// C3273.cpp
// compile with: /GX
int main()
{
   try
   {
   }
   catch (int)
   {
   }
   __finally   // C3273, remove __finally clause
   {
   }
}
```
