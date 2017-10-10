---
title: "編譯器錯誤 C2562 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2562
dev_langs:
- C++
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bcd98e241abd5cfd8cfce16224069470493d89b5
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2562"></a>編譯器錯誤 C2562
'identifier': 'void' 傳回值的函式  
  
 此函式宣告為`void`但傳回的值。  
  
 這個錯誤可能被因不正確的函式原型。  
  
 如果您在函式宣告中指定的傳回型別，可能會修正此錯誤。  
  
 下列範例會產生 C2562:  
  
```  
// C2562.cpp  
// compile with: /c  
void testfunc() {  
   int i;  
   return i;   // C2562 delete the return to resolve  
}  
```
