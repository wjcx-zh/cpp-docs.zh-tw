---
title: "編譯器錯誤 C3320 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3320"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3320"
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C3320
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 類型不可擁有與模組 'name' 屬性相同的名稱  
  
 匯出之使用者定義的類型 \(UDT\) 可以是結構、類別、列舉、等位或 [\_\_value](../../misc/value.md)，但不可以與傳遞至 [module](../../windows/module-cpp.md) 屬性 \(attribute\) 之 name 屬性 \(property\) 的參數同名。  
  
 下列範例會產生 C3320：  
  
```  
// C3320.cpp #include "unknwn.h" [module(name="xx")]; [export] struct xx {   // C3320 // Try the following line instead // [export] struct yy { int i; };  
```