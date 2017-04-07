---
title: "編譯器警告 （層級 3） C4280 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4280
dev_langs:
- C++
helpviewer_keywords:
- C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 086b9dfeaa2ae9ee8f48ad984505582efb32220d
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-level-3-c4280"></a>編譯器警告 (層級 3) C4280
'operator->' 透過為自我遞迴類型 'type'  
  
 您的程式碼錯誤地允許**-> 運算子**呼叫其本身。  
  
 下列範例會產生 C4280:  
  
```  
// C4280.cpp  
// compile with: /W3 /WX  
struct A  
{  
   int z;  
   A& operator ->();  
};  
  
void f(A y)  
{  
   int i = y->z; // C4280  
}  
```
