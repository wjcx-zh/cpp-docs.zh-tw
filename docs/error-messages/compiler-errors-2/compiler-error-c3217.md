---
title: "編譯器錯誤 C3217 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3217
dev_langs:
- C++
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b9122fc9c829ff017f717c2cec2d80dd254103ba
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3217"></a>編譯器錯誤 C3217
'param'：泛型參數不可在這項宣告中受到條件約束  
  
 條件約束格式不正確；泛型類別樣板參數必須與條件約束泛型參數一致。  
  
 下列範例會產生 C3217：  
  
```  
// C3217.cpp  
// compile with: /clr  
interface struct A {};  
  
generic <class T>  
ref class C {  
   generic <class T1>  
   where T : A   // C3217  
   void f();  
};  
```  
  
 下列範例示範可能的解決方式：  
  
```  
// C3217b.cpp  
// compile with: /clr /c  
interface struct A {};  
  
generic <class T>  
ref class C {  
   generic <class T1>  
   where T1 : A  
   void f();  
};  
```
