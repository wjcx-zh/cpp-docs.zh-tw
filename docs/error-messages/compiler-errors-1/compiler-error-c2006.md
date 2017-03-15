---
title: "編譯器錯誤 C2006 | Microsoft Docs"
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
  - "C2006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2006"
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'directive' : 必須有檔名，但只找到 'token'  
  
 指示詞 \(例如 [\#include](../../preprocessor/hash-include-directive-c-cpp.md) 或 [\#import](../../preprocessor/hash-import-directive-cpp.md)\) 需要一個檔名。  若要解決這種錯誤，請確認 *token* 是個有效的檔名。  此外，請將檔名放在雙引號或角括弧內。  
  
 下列範例會產生 C2006：  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 可能的解決方案：  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```