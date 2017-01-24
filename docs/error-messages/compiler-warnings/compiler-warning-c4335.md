---
title: "編譯器警告 C4335 | Microsoft Docs"
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
  - "C4335"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4335"
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4335
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵測到 Mac 檔案格式: 請將原始程式檔轉換為 DOS 或 UNIX 格式  
  
 原始程式檔第一行的行結束字元是 Macintosh 樣式 \(‘\\r’\) 而不是 UNIX \(‘\\n’\) 或 DOS \(‘\\r\\n’\)。  
  
 這項警告一律都以錯誤發出。如需有關如何停用這項警告的詳細資訊，請參閱 [warning](../../preprocessor/warning.md) pragma。此外，這項警告在每一次編譯中只發出一次。  因此如果有多個 `#include` 指示詞以 Macintosh 格式指定檔案，也只發出一次 C4335 警告。  
  
 以 Macintosh 格式產生檔案的其中一個方式是：使用 Visual Studio 中的 \[**進階儲存選項**\] \(在 \[**檔案**\] 功能表上\)。  
  
## 範例  
 下列範例會產生 C4335。  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```