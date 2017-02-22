---
title: "連結器工具錯誤 LNK1164 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1164"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1164"
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具錯誤 LNK1164
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

區段 section 對齊 \(number\) 大於 \/ALIGN 值  
  
 目的檔中的指定區段之對齊大小超出 [\/ALIGN](../../build/reference/align-section-alignment.md) 選項指定的值。  **\/ALIGN** 值必須為二次方，且必須等於或大於在目的檔中指定的區段對齊。  
  
 請重新以較小的區段對齊編譯，或是提高 **\/ALIGN** 的值。