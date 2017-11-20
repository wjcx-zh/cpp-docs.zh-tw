---
title: "break 陳述式 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: break
dev_langs: C++
helpviewer_keywords: break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a180c88fc71e4786e8512bc26421825132611ed4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="break-statement-c"></a>break 陳述式 (C)
`break` 陳述式會終止其所在最內層 `do`、`for`、`switch` 或 `while` 陳述式的執行。 程式控制權會轉移到終止陳述式之後的陳述式。  
  
## <a name="syntax"></a>語法  
 *jump-statement*：  
 `break;`  
  
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
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../cpp/break-statement-cpp.md)