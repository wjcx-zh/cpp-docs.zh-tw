---
title: "編譯器錯誤 C2584 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2584"
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'Class' : 直接基底類別 'Base2' 無法存取; 已經是 'Base1' 的基底類別  
  
 `Class` 已經直接從 `Base1` 衍生。  `Base2` 也已從 `Base1` 衍生。  `Class` 無法從 `Base2` 衍生，因為這樣一來就表示會再次 \(間接\) 從 `Base1` 繼承，這是不合法的，因為 `Base1` 已經是直接基底類別。  
  
## 範例  
 下列範例會產生 C2584。  
  
```  
// C2584.cpp  
// compile with: /c  
struct A1 {  
   virtual int MyFunction();  
};  
  
struct A2 {  
    virtual int MyFunction();  
};  
  
struct B1: public virtual A1, virtual A2 {  
    virtual int MyFunction();  
};  
  
struct B2: public virtual A2, virtual A1 {  
    virtual int MyFunction();  
};  
  
struct C: virtual B1, B2 {  
    virtual int MyFunction();  
};  
  
struct Z : virtual B2, virtual C {   // C2584  
// try the following line insted  
// struct Z : virtual C {  
    virtual int MyFunction();  
};  
```