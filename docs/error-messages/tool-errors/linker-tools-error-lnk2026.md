---
title: "連結器工具錯誤 LNK2026 | Microsoft Docs"
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
  - "LNK2026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2026"
ms.assetid: 9955bf7c-59b5-4fa1-8481-147db0d7df45
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模組對 SAFESEH 影像不安全  
  
 已指定 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)，但模組與安全例外狀況處理功能並不相容。  如果要配合 **\/SAFESEH** 使用此模組，則必須使用 Visual C\+\+ .NET 2003 \(含\) 以後版本之編譯器重新編譯此模組。