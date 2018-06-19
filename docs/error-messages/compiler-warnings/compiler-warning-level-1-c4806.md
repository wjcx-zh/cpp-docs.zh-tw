---
title: 編譯器警告 （層級 1） C4806 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92d5b36a653680285523c7cebb605238b37d57c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283389"
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