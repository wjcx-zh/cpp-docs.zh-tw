---
title: "MMWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MMWORD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MMWORD directive"
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MMWORD
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於 64 位元 MMX 和 SSE \(XMM\) 的指示以多媒體的運算元。  
  
## 語法  
  
```  
MMWORD  
```  
  
## 備註  
 `MMWORD`是一種。加到 MASM MMWORD，才能相等的功能已即可使用：  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 雖然這兩個指示從事 64 位元的運算元， `QWORD`是 64 位元不帶正負號整數的型別和`MMWORD`是 64 位元的多媒體值的型別。  
  
 `MMWORD`用來表示相同的型別[\_\_m64](../../cpp/m64.md)。  
  
## 範例  
  
```  
movq     mm0, mmword ptr [ebx]  
```