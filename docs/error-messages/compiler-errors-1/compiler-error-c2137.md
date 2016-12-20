---
title: "編譯器錯誤 C2137 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2137"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2137"
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2137
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

空白的字元常數  
  
 不允許空白的字元常數 \( ' ' \)。  
  
 下列範例會產生 C2137：  
  
```  
// C2137.cpp int main() { char c = '';   // C2137 char d = ' ';   // OK }  
```