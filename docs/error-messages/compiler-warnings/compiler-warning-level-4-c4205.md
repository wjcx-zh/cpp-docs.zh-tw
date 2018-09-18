---
title: 編譯器警告 （層級 4） C4205 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4205
dev_langs:
- C++
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9847e3c009e132993bcbb6aa94d2064d61e40421
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042360"
---
# <a name="compiler-warning-level-4-c4205"></a>編譯器警告 (層級 4) C4205

使用非標準擴充： 函式範圍中的靜態函式宣告

使用 Microsoft 擴充功能 (/Ze) 下**靜態**函式可以在另一個函式內宣告。 此函式有全域範圍。

## <a name="example"></a>範例

```
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。