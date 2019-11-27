---
title: 編譯器警告 (層級 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: b55594608eccc5d1e5e764bffb73ecb3787af1e4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541588"
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

**if** 陳述式比較指標 `pc` 中所儲存的值與字串 "Hello" 的位址，而這個位址是在每次字串出現在程式碼時個別配置。 **if** 陳述式不會比較 `pc` 所指向的字串與字串 "Hello"。

若要比較字串，請使用 `strcmp` 函式。