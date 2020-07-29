---
title: 編譯器警告 (層級 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 0d3b0aa05ca5fff16b3cd28c11e3bf8290de1b3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225341"
---
# <a name="compiler-warning-level-1-c4806"></a>編譯器警告 (層級 1) C4806

'operation': 不安全的作業：類型 'type' 升至類型 'type' 後沒有值可以等於所給的常數

此訊息會針對類似的程式碼發出警告 `b == 3` ，其中的 `b` 類型為 **`bool`** 。 升級規則會導致 **`bool`** 升級為 **`int`** 。 這是合法的，但絕不能這麼做 **`true`** 。 下列範例會產生 C4806：

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```
