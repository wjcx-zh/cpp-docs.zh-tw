---
title: "資源編譯器錯誤 RW2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2001"
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器錯誤 RW2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前置處理過的 RC 檔案中有無效的指示詞  
  
 RC 檔包含 **\#pragma** 指示詞。  
  
 使用帶有 **RC\_INVOKED** 常數 \(資源編譯器處理 Include 檔時所定義\) 的 **\#ifndef** 前置處理器指示詞。  將 **\#pragma** 指示詞置於定義 **RC\_INVOKED** 常數時未處理的程式碼區塊之中。  區塊中的程式碼只由 C\/C\+\+ 編譯器處理，而非資源編譯器。  以下範例程式碼則將這種技巧加以說明：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **\#pragma** 前置處理器指示詞在 .RC 檔中並無意義。   **\#include** 前置處理器指示詞則是經常使用在 .RC 檔中，用來包含標頭檔 \(無論是專案使用的自訂標頭檔 \(Header File\)，或是 Microsoft 在其產品中所提供的一個標準標頭檔\)。  這些包含檔之中有一些包含有 **\#pragma** 指示詞。  由於標頭檔可以包含一或多個其他標頭檔，因此可能不會立即發現包含有違規 **\#pragma** 指示詞的檔案。  
  
 **\#ifndef RC\_INVOKED** 技巧能夠在專案使用標頭檔中控制包含標頭檔。