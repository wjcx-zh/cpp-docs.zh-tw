---
title: 編譯器警告 （層級 1） C4129 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02f38044180c45e221099d2874b7f8ff48d62f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098442"
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