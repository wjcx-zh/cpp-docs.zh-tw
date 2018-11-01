---
title: 編譯器警告 (層級 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 8a3697b3bf63ac2a7a1e4e4bd0bf3a626c6bd631
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566123"
---
# <a name="compiler-warning-level-4-c4213"></a>編譯器警告 (層級 4) C4213

使用非標準擴充： 轉換值 （l-value）

您可以使用預設的 Microsoft 擴充功能 (/Ze) 中，轉換在指派陳述式左邊。

## <a name="example"></a>範例

```
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

這類轉換是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。