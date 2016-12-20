---
title: "編譯器錯誤 C2256 | Microsoft Docs"
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
  - "C2256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2256"
ms.assetid: 171fa2bc-8c72-49cd-afe5-d723b7acd3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 'function' 上使用 friend 規範不合法  
  
 不可將解構函式或建構函式指定為 [friend](../../cpp/friend-cpp.md)。  
  
 下列範例會產生 C2256：  
  
```  
// C2256.cpp  
// compile with: /c  
class C {  
public:  
   friend ~C();   // C2256  
   ~C();   // OK  
};  
```