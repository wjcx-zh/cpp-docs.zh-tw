---
title: break 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313359"
---
# <a name="break-statement-c"></a>break 陳述式 (C)

`break` 陳述式會終止其所在最內層 `do`、`for`、`switch` 或 `while` 陳述式的執行。 程式控制權會轉移到終止陳述式之後的陳述式。

## <a name="syntax"></a>語法

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**崩潰**

`break` 陳述式通常用來終止處理 `switch` 陳述式內的特定案例。 若缺少封閉迴圈，`switch` 陳述式會產生錯誤。

在巢狀陳述式中，`break` 陳述式只會終止 `do`、`for`、`switch` 或立即將它關閉的 `while` 陳述式。 您可以使用 `return` 或 `goto` 陳述式將控制轉移到巢狀結構之外的其他地方。

這個範例說明 `break` 陳述式：

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

## <a name="see-also"></a>請參閱

[break 語句](../cpp/break-statement-cpp.md)
