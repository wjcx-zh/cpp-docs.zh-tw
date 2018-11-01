---
title: 編譯器警告 （層級 2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 7d9a4ed09f026267e2c0f37fbbe4550ecd668dfc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514422"
---
# <a name="compiler-warning-level-2-c4156"></a>編譯器警告 （層級 2） C4156

刪除陣列運算式沒有使用陣列形式的 'delete';改用陣列形式

非陣列形式的**刪除**無法刪除陣列。 編譯器轉譯**刪除**以陣列形式。

只有在 Microsoft 擴充功能 (/Ze) 下，才會發生這個警告。

## <a name="example"></a>範例

```
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```