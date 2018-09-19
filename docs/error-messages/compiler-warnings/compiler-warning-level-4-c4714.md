---
title: 編譯器警告 （層級 4） C4714 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4714
dev_langs:
- C++
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecb9ecb1c73373ae96c92c911988a512e2173cec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136097"
---
# <a name="compiler-warning-level-4-c4714"></a>編譯器警告 (層級 4) C4714

函式 'function' 標記為 __forceinline 無法內嵌

內嵌展開，我們選取了指定的函式，但編譯器未進行內嵌。

雖然`__forceinline`會比對編譯器指出更強`__inline`、 內嵌仍然會由編譯器決定，會執行，但沒有啟發學習法會用來判斷受惠於內嵌此函式。

在某些情況下，編譯器不會內嵌特定函式機械的原因。 例如，編譯器不會內嵌：

- 如果這會導致混用 SEH 與 c + + EH 函式。

- 複製具有某些函式會建構-GX/EHs//eha 時，傳值方式傳遞的物件。

- -GX/EHs//eha 時，無法回溯物件傳回值的函式。

- 內嵌組譯碼不含-Og/Ox/O1/O2 編譯時使用的函式。

- 具有變數引數清單的函式。

- 具有的函式**嘗試**（c + + 例外狀況處理） 陳述式。

下列範例會產生 C4714:

```
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```