---
title: 編譯器警告（層級1） C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 1a48fc806f3274a59c99be25ac7a0e7b03a0454b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176217"
---
# <a name="compiler-warning-level-1-c4129"></a>編譯器警告（層級1） C4129

' character '：無法辨識的字元 escape 序列

字元或字串常數中的反斜線（\\）後面的 `character` 無法辨識為有效的逸出序列。 反斜線會被忽略，而且不會列印。 反斜線後面的字元會列印出來。

若要列印單一反斜線，請指定雙反斜線（\\\\）。

2\.13.2 C++一節中的標準會討論 escape 序列。

下列範例會產生 C4129：

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
