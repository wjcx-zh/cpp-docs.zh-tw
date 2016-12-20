---
title: "編譯器錯誤 C2190 | Microsoft Docs"
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
  - "C2190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2190"
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

第一次宣告的參數清單比第二次宣告的長  
  
 C 函式被以較短的參數清單宣告第二次。  C 並不支援多載函式。  
  
 下列範例會產生 C2190：  
  
```  
// C2190.c  
// compile with: /Za /c  
void func( int, float );  
void func( int  );   // C2190, different parameter list  
void func2( int  );   // OK  
```