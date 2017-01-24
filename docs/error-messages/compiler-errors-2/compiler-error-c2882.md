---
title: "編譯器錯誤 C2882 | Microsoft Docs"
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
  - "C2882"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2882"
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2882
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name' : 運算式中命名空間識別項的不合法使用  
  
 您嘗試在運算式中使用命名空間的名稱。  
  
 下列範例會產生 C2882：  
  
```  
// C2882.cpp  
// compile with: /c  
namespace A {  
   int k;  
}  
  
int i = A;   // C2882, can't assign A to i  
```