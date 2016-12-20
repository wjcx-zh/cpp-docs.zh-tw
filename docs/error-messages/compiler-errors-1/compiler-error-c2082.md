---
title: "編譯器錯誤 C2082 | Microsoft Docs"
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
  - "C2082"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2082"
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2082
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型式參數 'identifier' 重複定義  
  
 某個函式的型式參數已在函式主體內重新宣告。 若要解決此錯誤，請移除重複定義。  
  
 下列範例會產生 C2082：  
  
```  
// C2082.cpp void func(int i) { int i;   // C2082 int ii;   // OK }  
```