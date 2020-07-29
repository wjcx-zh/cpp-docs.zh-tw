---
title: 編譯器警告 (層級 1) C4155
ms.date: 11/04/2016
f1_keywords:
- C4155
helpviewer_keywords:
- C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
ms.openlocfilehash: 74369ce9eae123143caf15434506acf6e6e2e50e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223287"
---
# <a name="compiler-warning-level-1-c4155"></a>編譯器警告 (層級 1) C4155

刪除陣列運算式沒有使用陣列形式的 'delete'

的陣列形式 **`delete`** 應該用來刪除陣列。 這個警告只會在遵守 ANSI 相容性 (/Za) 時發生。

## <a name="example"></a>範例

下列範例會產生 C4155：

```cpp
// C4155.cpp
// compile with: /Za /W1
#include <stdio.h>

int main(void)
{
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];
    array[0][0] = 8;

    printf_s("%d\n", array[0][0]);

   delete array;   // C4155
    // try the following line instead
    // delete [] array;   // C4155
}
```
