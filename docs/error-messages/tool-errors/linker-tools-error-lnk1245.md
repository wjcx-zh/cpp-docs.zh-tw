---
title: "連結器工具錯誤 LNK1245 | Microsoft Docs"
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
  - "LNK1245"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1245"
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1245
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定的子系統 'subsystem' 無效；\/SUBSYSTEM 必須為 WINDOWS、WINDOWSCE 或 CONSOLE  
  
 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 是用來編譯物件，而且下列其中一個條件為 true：  
  
-   已定義了自訂進入點 \([\/ENTRY](../../build/reference/entry-entry-point-symbol.md)\)，以致連結器無法推斷子系統。  
  
-   已傳遞值給對 \/clr 物件無效的 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 連結器選項。  
  
 在上述兩種情況下，解決方式是指定有效的值給 \/SUBSYSTEM 連結器選項。