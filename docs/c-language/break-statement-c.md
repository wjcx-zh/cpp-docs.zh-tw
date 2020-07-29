---
title: break 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: c46173ceebd7291336c18d36203d1e4dc59ce46d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222000"
---
# <a name="break-statement-c"></a>break 陳述式 (C)

**`break`** 語句會終止執行其所在的最接近的封閉式 **`do`** 、、 **`for`** **`switch`** 或 **`while`** 語句。 程式控制權會轉移到終止陳述式之後的陳述式。

## <a name="syntax"></a>語法

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**崩潰**

**`break`** 語句經常用來終止語句內特定案例的處理 **`switch`** 。 缺少封閉式反復或語句會 **`switch`** 產生錯誤。

在 nested 語句中， **`break`** 語句只會終止 **`do`** 立即將其括住的、 **`for`** 、 **`switch`** 或 **`while`** 語句。 您可以使用 **`return`** 或 **`goto`** 語句，將控制項從嵌套結構外轉移到其他位置。

這個範例說明 **`break`** 語句：

```
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>另請參閱

[break 語句](../cpp/break-statement-cpp.md)
