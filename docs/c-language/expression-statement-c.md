---
title: "運算陳述式 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: ed9c2524c015faaf2aff4467e68d32c01bc31d61
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="expression-statement-c"></a>運算陳述式 (C)
執行運算陳述式時，會根據[運算式和指派](../c-language/expressions-and-assignments.md)中所列的規則，以求出運算式的值。  
  
## <a name="syntax"></a>語法  
 *expression-statement*:  
 *expression* opt**;**  
  
 在執行下一個陳述式之前，會完成運算式求值的所有副作用。 一個空的運算陳述式稱為 Null 陳述式。 如需詳細資訊，請參閱 [Null 陳述式](../c-language/null-statement-c.md)。  
  
 這些範例示範了運算陳述式。  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 在最後一個陳述式中，函式呼叫運算式、運算式的值 (包括由函式傳回的所有值) 會增加 3，然後指派給變數 `y` 和 `z`。  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../c-language/statements-c.md)
