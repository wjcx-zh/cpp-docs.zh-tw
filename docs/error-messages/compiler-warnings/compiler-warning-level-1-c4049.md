---
title: "編譯器警告 (層級 1) C4049 | Microsoft Docs"
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
  - "C4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4049"
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：終止行號發出  
  
 檔案包含超過 16,777,215 \(2<sup>24</sup>\-1\) 原始程式行。  編譯器在 16,777,215 停止編號。  
  
 對 16,777,215 行以後的程式碼：  
  
-   映像將不會包含這些行號的偵錯資訊。  
  
-   有些診斷可能會以不正確的行號報告。  
  
-   .asm 清單 \(\/FAs\) 可能會有不正確的行號。