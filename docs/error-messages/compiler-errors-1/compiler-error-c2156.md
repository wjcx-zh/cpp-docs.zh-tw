---
title: "編譯器錯誤 C2156 | Microsoft Docs"
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
  - "C2156"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2156"
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2156
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Pragma 必須定義在函式之外  
  
 必須在全域層級 \(函式主體外部\) 指定的 pragma 出現在函式內。  
  
 下列範例會產生 C2156：  
  
```  
// C2156.cpp #pragma optimize( "l", on )   // OK int main() { #pragma optimize( "l", on )   // C2156 }  
```