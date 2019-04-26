---
title: 編譯器警告 (層級 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: bef57d99ec9057f8b008deabda00b8a422a9e509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151691"
---
# <a name="compiler-warning-level-1-c4033"></a>編譯器警告 (層級 1) C4033

'function' 必須傳回值

函式未傳回值。 傳回未定義的值。

使用 `return` 而無傳回值的函式必須宣告為類型 `void`。

此錯誤適用於 C 語言程式碼。

下列範例會產生 C4033：

```
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