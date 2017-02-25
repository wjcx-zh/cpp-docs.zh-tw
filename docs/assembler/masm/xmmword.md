---
title: "XMMWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "XMMWORD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XMMWORD directive"
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# XMMWORD
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 128 位元 MMX 和 SSE \(XMM\) 的指示以多媒體的運算元。  
  
## 語法  
  
```  
XMMWORD  
```  
  
## 備註  
 `XMMWORD`用來表示相同的型別[\_\_m128](../../cpp/m128.md)。  
  
## 範例  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```