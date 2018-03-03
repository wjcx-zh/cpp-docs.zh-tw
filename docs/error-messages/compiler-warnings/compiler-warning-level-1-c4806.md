---
title: "編譯器警告 （層級 1） C4806 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bddda6bd683133f278f79544b2bf13aa132e131
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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