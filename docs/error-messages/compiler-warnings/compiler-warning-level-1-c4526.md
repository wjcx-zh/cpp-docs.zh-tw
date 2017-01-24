---
title: "編譯器警告 (層級 1) C4526 | Microsoft Docs"
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
  - "C4526"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4526"
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4526
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 靜態成員函式無法覆寫虛擬函式，'virtual function' 會忽略覆寫並隱藏虛擬函式  
  
 靜態成員函式符合覆寫虛擬函式的條件，使成員函式同時為虛擬與靜態的。  
  
 下列程式碼會產生 C4526：  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 以下是可能的修復方式：  
  
-   如果函式是要覆寫基底類別虛擬函式，請移除靜態的規範。  
  
-   如果函式是要成為靜態成員函式，請重新命名，它才不會與基底類別虛擬函式衝突。