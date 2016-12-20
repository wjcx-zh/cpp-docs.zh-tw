---
title: "編譯器錯誤 C2458 | Microsoft Docs"
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
  - "C2458"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2458"
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2458
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 定義中的重複定義  
  
 類別、結構、等位或列舉型別 \(Enumeration\) 重新定義於自己的宣告中。  
  
 下列範例會產生 C2458：  
  
```  
// C2458.cpp  
class C {  
   enum i { C };   // C2458  
};  
```