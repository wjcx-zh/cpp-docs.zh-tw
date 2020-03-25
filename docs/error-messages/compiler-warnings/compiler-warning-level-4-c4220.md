---
title: 編譯器警告 (層級 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 90b66a9d819d3014c1e1437b691766ade420bd4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161252"
---
# <a name="compiler-warning-level-4-c4220"></a>編譯器警告 (層級 4) C4220

varargs 符合剩餘的參數

在預設的 Microsoft 擴充功能（/Ze）底下，函式的指標會與具有類似但變數之引數的函式指標相符。

## <a name="example"></a>範例

```c
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

這類指標與 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）不相符。
