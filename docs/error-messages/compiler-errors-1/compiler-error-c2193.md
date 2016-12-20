---
title: "編譯器錯誤 C2193 | Microsoft Docs"
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
  - "C2193"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2193"
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2193
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 已經在區段中  
  
 使用 `alloc_text` 和 `code_seg` pragma，將函式放入兩個不同的區段內。  
  
 下列範例會產生 C2193：  
  
```  
// C2193.cpp  
// compile with: /c  
extern "C" void MYFUNCTION();  
#pragma alloc_text(MYCODE, MYFUNCTION)  
#pragma code_seg("MYCODE2")  
extern "C" void MYFUNCTION() {}   // C2193  
extern "C" void MYFUNCTION2() {}  
```