---
title: "編譯器錯誤 C2506 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2506"
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器錯誤 C2506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : '\_\_declspec\(modifier\)' 不可套用至這個符號  
  
 您不能為一個 Managed 類別的靜態成員宣告處理序專屬或 per\-appdomain。  
  
 如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)。  
  
## 範例  
 下列範例會產生 C2506。  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```