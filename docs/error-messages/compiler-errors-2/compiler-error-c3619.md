---
title: "編譯器錯誤 C3619 | Microsoft Docs"
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
  - "C3619"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3619"
ms.assetid: 76ae80d0-9fbe-4297-a1ef-b1503377fdcf
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3619
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在 Managed 或 WinRT 類型中宣告範本  
  
 不允許在 Managed 或 WinRT 類別或介面中使用類別樣板。  
  
 僅可使用 **\/clr:oldSyntax** 連接 C3619。  
  
 下列範例會產生 C3619：  
  
```  
// C3619.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc class X {  
   template<typename T> class Y {   // C3619  
   };  
};  
```