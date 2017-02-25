---
title: "編譯器錯誤 C2007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2007"
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#define 語法  
  
 `#define` 後未出現任何識別項。  若要解決這種錯誤，請使用識別項。  
  
 下列範例會產生 C2007：  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 可能的解決方案：  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```