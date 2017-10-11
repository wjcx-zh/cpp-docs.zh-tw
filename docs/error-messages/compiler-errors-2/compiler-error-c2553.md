---
title: "編譯器錯誤 C2553 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 623a09c54333ef62de7a7924cc4be02ff1b2c726
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2553"></a>編譯器錯誤 C2553
'base_function': 覆寫虛擬函式傳回類型不同於 'override_function'  
  
 在衍生類別中的函式嘗試覆寫虛擬函式中的基底類別，但在衍生的類別函式沒有基底類別函式相同的傳回型別。  覆寫函式簽章必須符合覆寫的函式簽章。  
  
 下列範例會產生 C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```
