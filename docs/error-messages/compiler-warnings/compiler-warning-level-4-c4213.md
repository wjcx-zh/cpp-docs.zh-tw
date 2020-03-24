---
title: 編譯器警告 (層級 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: e462fcc2d0283d2519796127612123f7d792d00e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161291"
---
# <a name="compiler-warning-level-4-c4213"></a>編譯器警告 (層級 4) C4213

使用非標準的擴充：左值上的轉換

使用預設的 Microsoft 擴充功能（/Ze）時，您可以在指派語句的左側使用轉換。

## <a name="example"></a>範例

```c
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

這類轉換在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下是不正確。
