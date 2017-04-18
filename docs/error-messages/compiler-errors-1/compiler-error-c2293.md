---
title: "編譯器錯誤 C2293 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2293
dev_langs:
- C++
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 517f2f31c012f3d8c45fdd93fb2132b12bddd229
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2293"></a>編譯器錯誤 C2293
'identifier': 將 __based 規範作為成員變數不合法  
  
 `__based` 修飾詞的規範必須是非成員的指標。  
  
 下列範例會產生 C2293：  
  
```  
// C2293.cpp  
// compile with: /c  
class A {  
   static int *i;  
   void __based(i) *bp;   // C2293  
   void *bp2;   // OK  
};  
```
