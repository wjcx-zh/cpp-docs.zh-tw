---
title: "編譯器警告 （層級 4） C4130 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 32ec1055c5da769c026b778897a5bd9b741b2d40
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4130"></a>編譯器警告 (層級 4) C4130
'operator': 以字串常數的位址進行邏輯運算  
  
 搭配使用運算子與字串常值的位址會產生非預期的程式碼。  
  
 下列範例會產生 C4130：  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 **if** 陳述式比較指標 `pc` 中所儲存的值與字串 "Hello" 的位址，而這個位址是在每次字串出現在程式碼時個別配置。 **if** 陳述式不會比較 `pc` 所指向的字串與字串 "Hello"。  
  
 若要比較字串，請使用 `strcmp` 函式。
