---
title: "for 陳述式 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13d292cebbb8aa3aa6a65fbc41b8b38934732b5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="for-statement-c"></a>for 陳述式 (C)
**for** 陳述式可讓您依指定的次數重複執行陳述式或複合陳述式。 **for** 陳述式的主體會執行零或多次，直到的選擇性條件變成 false 為止。 您可以在 **for** 陳述式內使用選擇性的運算式，在 **for** 陳述式的執行期間進行初始化和變更值。  
  
## <a name="syntax"></a>語法  
 *iteration-statement*：  
 &nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*  
  
 **for** 陳述式的執行如下所述：  
  
1.  會對 *init-expression* 進行評估 (如果有的話)。 這會指定迴圈的初始化。 *init-expression* 的類型沒有限制。  
  
2.  會對 *cond-expression* 進行評估 (如果有的話)。 此運算式必須是算術或指標類型。 在每個反覆項目之前進行評估。 有三個可能的結果：  
  
    -   如果 *cond-expression* 為 **true** (非零值)，則會執行 *statement*，接著執行 *loop-expression* (如果有的話)。 在每次反覆運算之後，都會評估 *loop-expression*。 其類型沒有限制。 副作用將會依順序執行。 接著會從 *cond-expression* 的評估重新開始此程序。  
  
    -   如果省略 *cond-expression*，則 *cond-expression* 會被視為 true，並依如前面段落中所述的方式繼續執行。 只有在陳述式主體內的 **break** or **return** 陳述式執行時，或 **goto** (移至 **for** 陳述式主體外部的標籤陳述式) 時，沒有 *cond-expression* 引數的 **for** 陳述式才會終止。  
  
    -   如果 *cond-expression* 為 **false** (0)，**for** 陳述式的執行會終止，而並將控制項傳遞至程式中的下一個陳述式。  
  
 在陳述式主體中執行 **break**、**goto** 或 **return** 陳述式時，**for** 陳述式也可能會終止。 **for** 迴圈中的 **continue** 陳述式會評估 *loop-expression*。 **for** 迴圈內部的 **break** 陳述式執行時，不會評估也不會執行 *loop-expression*。 此陳述式  
  
```  
for( ;; )  
```  
  
 是產生無限迴圈的慣用方法，其只能使用 **break**、**goto** 或 **return** 陳述式來結束。  
  
## <a name="code"></a>程式碼  
 這個範例說明 **for** 陳述式：  
  
```  
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
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../c-language/statements-c.md)