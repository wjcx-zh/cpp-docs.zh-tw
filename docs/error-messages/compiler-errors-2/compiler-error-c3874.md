---
title: "編譯器錯誤 C3874 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3874"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3874"
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3874
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 的傳回型別應該是 'int'，而非 'type'  
  
 函式沒有編譯器必須有的傳回型別。  
  
 下列範例會產生 C3874：  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```