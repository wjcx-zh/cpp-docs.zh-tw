---
title: 編譯器警告 （層級 4） C4213 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4213
dev_langs:
- C++
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59bb2d8b2c25516558c4810d190f0bec9b98c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025607"
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