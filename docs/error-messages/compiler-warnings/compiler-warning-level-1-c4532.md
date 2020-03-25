---
title: 編譯器警告 (層級 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: 97ef7093aa56b41b869979e09d77fc448c6cf43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186435"
---
# <a name="compiler-warning-level-1-c4532"></a>編譯器警告 (層級 1) C4532

[繼續]：跳出 __finally/finally 組塊在終止處理期間有未定義的行為

編譯器遇到下列其中一個關鍵字：

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

導致在異常終止期間跳出[__finally](../../cpp/try-finally-statement.md)或[finally](../../dotnet/finally.md)區塊。

如果發生例外狀況，而且堆疊在執行終止處理常式（`__finally` 或 finally 區塊）期間已被展開，而您的程式碼在 `__finally` 區塊結束之前跳出 `__finally` 區塊，則行為是未定義的。 控制項可能不會回到回溯程式碼，因此例外狀況可能無法正確處理。

如果您必須跳出 **__finally**區塊，請先檢查是否有異常終止。

下列範例會產生 C4532;只要將跳躍語句標記為批註即可解決警告。

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```
