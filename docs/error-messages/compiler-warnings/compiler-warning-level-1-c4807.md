---
title: 編譯器警告 (層級 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 17a33f7c55fa2825eae1c7d8b9d8ab78e4ed5274
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225328"
---
# <a name="compiler-warning-level-1-c4807"></a>編譯器警告 (層級 1) C4807

'operation' : 不安全的混用類型 'type' 和類型 'type' 的已簽名位元欄位

將一個位帶正負號的位欄位與變數進行比較時，會產生這個警告 **`bool`** 。 因為一個位的帶正負號的位欄位只能包含值-1 或0，所以與比較危險 **`bool`** 。 不會產生混合 **`bool`** 和一位不帶正負號位欄位的警告，因為它們與相同 **`bool`** ，而且只能保留0或1。

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
