---
title: "編譯器錯誤 C3812 | Microsoft Docs"
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
  - "C3812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3812"
ms.assetid: 326ac706-9a5f-4851-b9d2-b90c64c75532
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_property' 必須是屬性宣告中的第一個語彙基元  
  
 宣告屬性時，[\_\_property](../../misc/property.md) 關鍵字必須是行中的第一個語彙基元。  
  
 C3812 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3812：  
  
```  
// C3812.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
  
__gc class X {  
   static __property int get_Size() { // C3812, remove static specifier  
      return 0;  
   }  
};  
```