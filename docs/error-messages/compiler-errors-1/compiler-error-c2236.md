---
title: "編譯器錯誤 C2236 | Microsoft Docs"
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
  - "C2236"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2236"
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2236
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的語彙基元 'identifier'。您是否忘記 ';'？  
  
 已經將識別項定義為類型，且無法由使用者定義類型覆寫。  
  
 下列範例會產生 C2236：  
  
```  
// C2236.cpp  
// compile with: /c  
int class A {};  // C2236 "int class" is unexpected  
int i;  
class B {};  
```