---
title: "編譯器錯誤 C2379 | Microsoft Docs"
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
  - "C2379"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2379"
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2379
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

升級時型式參數 number 具有不同的型別  
  
 經由預設的升級後，指定參數的型別和先前宣告的型別並不相容。  這是 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 中的錯誤，並且是 Microsoft 擴充功能 \(**\/Ze**\) 的警告。  
  
 下列範例會產生 C2379：  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```