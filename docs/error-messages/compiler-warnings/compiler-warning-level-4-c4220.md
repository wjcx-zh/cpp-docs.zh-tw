---
title: 編譯器警告 (層級 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 177fb01ba4181f72740724d107fe08e6680ed492
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401107"
---
# <a name="compiler-warning-level-4-c4220"></a>編譯器警告 (層級 4) C4220

varargs 符合剩餘的參數

在預設的 Microsoft 擴充功能 (/Ze) 中，函式的指標會比對類似，但變數、 引數的函式的指標。

## <a name="example"></a>範例

```
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

這類指標不符合 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。