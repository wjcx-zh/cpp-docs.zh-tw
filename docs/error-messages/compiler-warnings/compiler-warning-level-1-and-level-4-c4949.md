---
title: "編譯器警告 (層級 1 和層級 4) C4949 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4949"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4949"
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1 和層級 4) C4949
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

pragma 'managed' 和 'unmanaged' 只有在以 '\/clr\[:option\]' 編譯時才有意義  
  
 如果原始程式碼不是使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯，編譯器會忽略 [managed](../../preprocessor/managed-unmanaged.md) 和 unmanaged pragmas。  這項警告僅供參考，  
  
 下列範例會產生 C4949：  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 使用 **\#pragma unmanaged** 而不加 **\/clr** 時，C4949 是層級 4 警告。  
  
 下列範例會產生 C4949：  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```