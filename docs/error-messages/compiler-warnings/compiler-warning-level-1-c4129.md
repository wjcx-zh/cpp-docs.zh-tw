---
title: 編譯器警告 （層級 1） C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: dc4f4c4c1feeba543ce0baa71e1ee5dfd81fdcae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428662"
---
# <a name="compiler-warning-level-1-c4129"></a>編譯器警告 （層級 1） C4129

'character': 無法辨識的字元逸出序列

`character`反斜線 (\\) 中的字元或字串常數無法辨識為有效的逸出序列。 反斜線會略過，而且不會列印。 反斜線後面的字元會列印。

若要列印單一反斜線，請指定 雙反斜線 (\\\\)。

C + + 標準，在 2.13.2 討論逸出序列。

下列範例會產生 C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```