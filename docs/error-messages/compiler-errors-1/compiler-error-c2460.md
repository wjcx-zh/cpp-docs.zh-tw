---
title: "編譯器錯誤 C2460 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 00e4015a0dae5054973ba72bb0e4f89c7443ae03
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2460"></a>編譯器錯誤 C2460
'identifier1': 使用 'identifier2'，已經定義的  
  
 類別或結構 (`identifier2`) 宣告為本身的成員 (`identifier1`)。 不允許遞迴定義的類別和結構。  
  
 下列範例會產生 C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 相反地，在類別中使用指標參考。  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```
