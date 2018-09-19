---
title: 編譯器警告 （層級 4） C4220 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4220
dev_langs:
- C++
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70c6b104c924a09570d4bd77191f1df715726370
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118774"
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