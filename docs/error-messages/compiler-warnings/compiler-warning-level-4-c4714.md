---
title: 編譯器警告 (層級 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 286a9e6e12643d3dadd070e7c4cf4b2dd350c02c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219855"
---
# <a name="compiler-warning-level-4-c4714"></a>編譯器警告 (層級 4) C4714

> 函式 ' function ' 標記為 __forceinline 不是內嵌的

已選取指定的函式來進行內嵌展開，但編譯器未執行內嵌功能。

雖然 **`__forceinline`** 比更強大的編譯器指示 **`__inline`** ，但是在編譯器時仍會自行執行內嵌，但不會使用啟發學習法來判斷內嵌此函式的優點。

在某些情況下，編譯器不會針對機械原因內嵌特定函式。 例如，編譯器不會內嵌：

- 函式，如果它會導致同時混用 SEH 和 c + + EH。

- 當-GX/EHs/EHa 為 on 時，某些具有複製結構化物件的函式會以傳值方式傳遞。

- 當-GX/EHs/EHa 為 on 時，函數會以傳值方式傳回 unwindable 物件。

- 不使用-Og/Ox/O1/O2 編譯時，具有內嵌組解碼的函式。

- 具有可變引數清單的函式。

- 具有 **`try`** （c + + 例外狀況處理）語句的函式。

下列範例會產生 C4714：

```cpp
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
