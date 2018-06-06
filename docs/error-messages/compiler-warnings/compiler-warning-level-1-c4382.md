---
title: 編譯器警告 （層級 1） C4382 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29afe066fb86d0dd99216a63c057046ec76de55b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704317"
---
# <a name="compiler-warning-level-1-c4382"></a>編譯器警告 (層級 1) C4382

> 擲回 '*類型*': 具有 __clrcall 解構函式或複製建構函式的型別只會攔截在 /clr: pure 模組

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

編譯時 **/clr** (不 **/clr: pure**)，例外狀況處理為原生類型中預期的成員函式[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md). 原生類型與成員函式使用`__clrcall`無法攔截在編譯的模組中的呼叫慣例 **/clr**。

如果將編譯的模組中攔截例外狀況 **/clr: pure**，您可以忽略此警告。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C4382。

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```