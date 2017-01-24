---
title: "編譯器錯誤 C2191 | Microsoft Docs"
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
  - "C2191"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2191"
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2191
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

第二次宣告的參數清單比第一次宣告的長  
  
 C 函式被以較長的參數清單宣告第二次。  C 並不支援多載函式。  
  
## 範例  
 下列範例會產生 C2191：  
  
```  
// C2191.c  
// compile with: /Za /c  
void func( int );  
void func( int, float );   // C2191 different parameter list  
void func2( int, float );   // OK  
```