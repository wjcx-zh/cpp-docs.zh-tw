---
title: break 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: 5322f8cb5218882d891e2cd66704f9dbfd1bc149
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683464"
---
# <a name="break-statement-c"></a>break 陳述式 (C)

**`break`** 語句會終止執行最接近的封閉 **`do`** 、 **`for`** 、 **`switch`** 或 **`while`** 語句。 程式控制權會轉移到終止陳述式之後的陳述式。

## <a name="syntax"></a>語法

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**折**

**`break`** 語句經常用來終止語句中特定案例的處理 **`switch`** 。 缺少封閉的反復或 **`switch`** 語句會產生錯誤。

在嵌套的語句中， **`break`** 語句只會 **`do`** 終止 **`for`** 立即封閉的、、 **`switch`** 或 **`while`** 語句。 您可以使用 **`return`** 或 **`goto`** 語句，將控制項移到其他位置，而不是嵌套結構。

此範例說明 **`break`** 語句：

```C
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
