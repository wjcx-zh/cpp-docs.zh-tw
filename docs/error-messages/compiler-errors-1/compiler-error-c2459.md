---
title: "編譯器錯誤 C2459 | Microsoft Docs"
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
  - "C2459"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2459"
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2459
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 已經定義; 無法以匿名成員加入  
  
 類別、結構或等位透過匿名等位的成員，重新定義於自己的範圍 \(Scope\) 內。  
  
 下列範例會產生 C2459：  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```