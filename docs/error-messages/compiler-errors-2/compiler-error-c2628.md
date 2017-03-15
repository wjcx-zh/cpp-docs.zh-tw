---
title: "編譯器錯誤 C2628 | Microsoft Docs"
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
  - "C2628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2628"
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1' 之後接 'type2' 不合法 \(您是否遺忘 ';'?\)  
  
 可能是遺漏分號。  
  
 下列範例會產生 C2628：  
  
```  
// C2628.cpp  
class CMyClass {}  
int main(){}   // C2628 error  
```  
  
 可能的解決方案：  
  
```  
// C2628b.cpp  
class CMyClass {};  
int main(){}  
```