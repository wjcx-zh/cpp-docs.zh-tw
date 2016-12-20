---
title: "編譯器錯誤 C2793 | Microsoft Docs"
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
  - "C2793"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2793"
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2793
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'token' : '::' 之後未預期的語彙基元，必須是識別項或關鍵字 'operator'  
  
 識別項或關鍵字 `operator` 是唯一可以跟隨在 `__super::` 之後的語彙基元。  
  
 下列範例會產生 C2793  
  
```  
// C2793.cpp  
struct B {  
   void mf();  
};  
  
struct D : B {  
   void mf() {  
      __super::(); // C2793  
   }  
};  
```