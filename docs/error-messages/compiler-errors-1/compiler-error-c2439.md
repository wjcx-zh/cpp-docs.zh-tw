---
title: "編譯器錯誤 C2439 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2439"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2439"
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2439
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 無法將成員初始化  
  
 類別、結構或等位的成員無法初始化。  
  
### 若要修正，請檢查下列可能原因  
  
1.  嘗試初始化間接基底類別 \(Base Class\) 或結構。  
  
2.  嘗試初始化類別或結構的繼承成員。  繼承的成員必須由類別或結構的建構函式來初始化。