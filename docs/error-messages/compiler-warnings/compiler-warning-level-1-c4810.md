---
title: "編譯器警告 (層級 1) C4810 | Microsoft Docs"
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
  - "C4810"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4810"
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4810
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

pragma pack\(show\) 的值 \=\= n  
  
 當您使用 [pack](../../preprocessor/pack.md) pragma 的 **show** 選項時，會發出這個警告。*n* 是目前的 pack 值。  
  
 例如，下列程式碼顯示 C4810 警告如何使用 pack pragma：  
  
```  
// C4810.cpp // compile with: /W1 /LD // C4810 expected #pragma pack(show) #pragma pack(4) #pragma pack(show)  
```