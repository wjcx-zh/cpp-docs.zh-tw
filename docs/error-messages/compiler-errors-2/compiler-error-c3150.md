---
title: "編譯器錯誤 C3150 | Microsoft Docs"
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
  - "C3150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3150"
ms.assetid: c1ff28f5-52fe-4fd4-81d0-2e0ad8548631
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'element' : 'attribute' 只可以套用至類別、介面、陣列或指標  
  
 [\_\_gc](../../misc/gc.md) 只能使用於類別、介面或陣列。  
  
 C3150 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3150：  
  
```  
// C3150.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc void f()   // C3150; function cannot be managed  
{  
}  
```