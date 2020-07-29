---
title: 編譯器警告（層級2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 279ab5d9de738fb4e2aa6dece4bb16353eca031b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206480"
---
# <a name="compiler-warning-level-2-c4156"></a>編譯器警告（層級2） C4156

刪除陣列運算式而不使用陣列形式的 ' delete ';替代的陣列表單

的非陣列形式 **`delete`** 無法刪除陣列。 編譯器已轉譯 **`delete`** 為數組表單。

只有在 Microsoft extensions （/Ze）底下才會發生此警告。

## <a name="example"></a>範例

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```
