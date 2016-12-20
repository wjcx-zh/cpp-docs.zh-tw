---
title: "編譯器警告 C4956 | Microsoft Docs"
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
  - "C4956"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4956"
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4956
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 這個類型無法驗證  
  
 指定 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 且您的程式碼包含無法驗證的類型時，就會產生這個警告。  
  
 如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [\/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。  
  
 下列範例會產生 C4956：  
  
```  
// C4956.cpp // compile with: /clr:safe int* p;   // C4956  
```