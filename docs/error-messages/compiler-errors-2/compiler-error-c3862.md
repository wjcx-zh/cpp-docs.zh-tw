---
title: "編譯器錯誤 C3862 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3862"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3862"
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3862
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 不能以 \/clr:pure 或 \/clr:safe 編譯 Unmanaged 函式  
  
 以 **\/clr:pure** 或 **\/clr:safe** 編譯將產生只有 MSIL 的影像，也就是沒有原生 \(Unmanaged\) 程式碼的影像。因此，您不能在 **\/clr:pure** 或 **\/clr:safe**  編譯中使用 `unmanaged` pragma。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)與[managed、unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
## 範例  
 下列範例會產生 C3862：  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```