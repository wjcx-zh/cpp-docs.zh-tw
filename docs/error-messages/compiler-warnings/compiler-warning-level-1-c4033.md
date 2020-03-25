---
title: 編譯器警告 (層級 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164348"
---
# <a name="compiler-warning-level-1-c4033"></a>編譯器警告 (層級 1) C4033

'function' 必須傳回值

函式未傳回值。 傳回未定義的值。

使用 `return` 而無傳回值的函式必須宣告為類型 `void`。

此錯誤適用於 C 語言程式碼。

下列範例會產生 C4033：

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
