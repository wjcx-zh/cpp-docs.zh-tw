---
title: 編譯器警告 （層級 2） C4156 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eddce0944152fe95aa4ef2fd98ec30a793a90978
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084493"
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