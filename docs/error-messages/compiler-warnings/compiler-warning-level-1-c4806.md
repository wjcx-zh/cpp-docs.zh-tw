---
title: "編譯器警告 （層級 1） C4806 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 021b0a5fd91df53e8fd1cb297c5d697f7135ff89
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4806"></a>編譯器警告 (層級 1) C4806
'operation': 不安全的作業：類型 'type' 升至類型 'type' 後沒有值可以等於所給的常數  
  
 這個訊息會對程式碼 (例如 `b == 3`) 發出警告，而在程式碼中， `b` 具有類型 `bool`。 提升規則可讓 `bool` 提升成 `int`。 這是合法的，但絕不可為 **true**。 下列範例會產生 C4806：  
  
```  
// C4806.cpp  
// compile with: /W1  
int main()  
{  
   bool b = true;  
   // try..  
   // int b = true;  
  
   if (b == 3)   // C4806  
   {  
      b = false;  
   }  
}  
```
