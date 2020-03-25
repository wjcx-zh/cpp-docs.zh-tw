---
title: 編譯器警告 (層級 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 2424d076be0914a68c3227566cb851b7ab64cc0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175034"
---
# <a name="compiler-warning-level-1-c4807"></a>編譯器警告 (層級 1) C4807

'operation' : 不安全的混用類型 'type' 和類型 'type' 的已簽名位元欄位

比較一位元帶正負號位元欄位與 `bool` 變數時，會產生這個警告。 因為一位元帶正負號位元欄位只能包含值 -1 或 0，所以比較它與 `bool`十分危險。 不會產生有關混合使用 `bool` 與一位元未帶正負號位元欄位的警告，因為它們與 `bool` 相同，而且只能保留 0 或 1。

## <a name="example"></a>範例

下列範例會產生 C4807：

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
