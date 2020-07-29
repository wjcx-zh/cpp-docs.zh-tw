---
title: 編譯器警告 (層級 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 7b2fbccfd3b124220d6e310c01adace1d3e112c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219959"
---
# <a name="compiler-warning-level-4-c4130"></a>編譯器警告 (層級 4) C4130

'operator': 以字串常數的位址進行邏輯運算

搭配使用運算子與字串常值的位址會產生非預期的程式碼。

下列範例會產生 C4130：

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

**`if`** 語句會比較指標中所儲存的值 `pc` 與字串 "Hello" 的位址，這會在每次字串出現在程式碼時個別配置。 **`if`** 語句不會比較所指向的字串 `pc` 與字串 "Hello"。

若要比較字串，請使用 `strcmp` 函式。
