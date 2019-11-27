---
title: 編譯器警告 (層級 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 318b228a1af17543062943a336ccccd06bc6ae46
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541817"
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