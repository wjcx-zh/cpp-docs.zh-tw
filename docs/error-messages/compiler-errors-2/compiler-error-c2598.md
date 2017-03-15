---
title: "編譯器錯誤 C2598 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2598"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2598"
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2598
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

連結規格必須在全域範圍內  
  
 連結規範 \(Linkage Specifier\) 宣告在區域範圍內。  
  
 下列範例會產生 C2598：  
  
```  
// C2598.cpp  
// compile with: /c  
void func() {  
   extern "C" int func2();   // C2598  
}  
  
extern "C" int func( int i );  
```