---
title: "編譯器錯誤 C2553 | Microsoft Docs"
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
  - "C2553"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2553"
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2553
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'base\_function': 覆寫虛擬函式傳回型別不同於 'override\_function'  
  
 衍生類別中的函式試圖覆寫基底類別中的虛擬函式，但衍生類別函式沒有與基底類別函式相同的傳回型別。覆寫函式簽章必須符合正在加以覆寫之函式的簽章。  
  
 下列範例會產生 C2553：  
  
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