---
title: for 陳述式 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: 91675fbe15ec6abf5aae4548990d9b4e0703e967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229723"
---
# <a name="for-statement-c"></a>for 陳述式 (C)

**`for`** 語句可讓您以指定的次數重複語句或複合陳述式。 語句的主體 **`for`** 會執行零次或多次，直到選擇性條件變成 false 為止。 您可以在語句內使用選擇性的運算式，在 **`for`** 語句的執行期間初始化和變更值 **`for`** 。

## <a name="syntax"></a>語法

*反復專案語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`for`****（** *init 運算式*<sub>opt</sub> **;** *導線運算式*<sub>opt</sub> **;** *迴圈運算式*<sub>opt</sub> **）** *語句*

語句的執行如下 **`for`** 所示：

1. 會對 *init-expression* 進行評估 (如果有的話)。 這會指定迴圈的初始化。 *init-expression* 的類型沒有限制。

1. 會對 *cond-expression* 進行評估 (如果有的話)。 此運算式必須是算術或指標類型。 在每個反覆項目之前進行評估。 有三個可能的結果：

   - 如果*導線運算式*為 **`true`** （非零），則會執行*語句*，然後評估*迴圈運算式*（如果有的話）。 在每次反覆運算之後，都會評估 *loop-expression*。 其類型沒有限制。 副作用將會依順序執行。 接著會從 *cond-expression* 的評估重新開始此程序。

   - 如果省略 *cond-expression*，則 *cond-expression* 會被視為 true，並依如前面段落中所述的方式繼續執行。 **`for`** 只有在*cond-expression* **`break`** **`return`** 執行語句主體內的或語句，或 **`goto`** 執行（對語句主體以外的標記語句）時，沒有導線運算式引數的語句才會終止 **`for`** 。

   - 如果*導線運算式*為 **`false`** （0），則語句的執行會 **`for`** 終止，並將控制權傳遞至程式中的下一個語句。

**`for`** 當 **`break`** **`goto`** 語句主體內的、或語句執行時，語句也 **`return`** 會終止。 **`continue`** 迴圈中的語句 **`for`** 會導致評估*迴圈運算式*。 當 **`break`** 語句在迴圈內執行時 **`for`** ，不會評估或執行*迴圈運算式*。 此陳述式

```C
for( ; ; )
```

是產生無限迴圈的慣用方法，只能以 **`break`** 、 **`goto`** 或語句來結束 **`return`** 。

## <a name="example"></a>範例

這個範例說明 **`for`** 語句：

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>輸出

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>另請參閱

[陳述式](../c-language/statements-c.md)
