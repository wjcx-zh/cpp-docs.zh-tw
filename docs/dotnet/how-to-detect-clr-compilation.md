---
title: "如何：偵測 /clr 編譯 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 偵測使用"
  - "編譯, 偵測 /clr"
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：偵測 /clr 編譯
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 `_MANAGED` 或 `_M_CEE` 巨集以查看模組是否使用 **\/clr** 進行編譯。  如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如需巨集的詳細資訊，請參閱[預先定義的巨集](../preprocessor/predefined-macros.md)。  
  
## 範例  
  
```  
// detect_CLR_compilation.cpp  
// compile with: /clr  
#include <stdio.h>  
  
int main() {  
   #if (_MANAGED == 1) || (_M_CEE == 1)  
      printf_s("compiling with /clr\n");  
   #else  
      printf_s("compiling without /clr\n");  
   #endif  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)