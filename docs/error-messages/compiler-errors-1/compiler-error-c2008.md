---
title: "編譯器錯誤 C2008 | Microsoft Docs"
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
  - "C2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2008"
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'character' : 未預期在巨集定義中  
  
 此字元立即出現在巨集名稱後面。  若要解決這種錯誤，巨集名稱後面必須加入空格。  
  
 下列範例會產生 C2008：  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 可能的解決方案：  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```