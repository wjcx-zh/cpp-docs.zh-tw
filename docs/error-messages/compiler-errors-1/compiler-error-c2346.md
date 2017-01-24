---
title: "編譯器錯誤 C2346 | Microsoft Docs"
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
  - "C2346"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2346"
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2346
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 無法編譯為原生: 原因  
  
 編譯器無法將函式編譯為 MSIL。  
  
 如需詳細資訊，請參閱[managed、unmanaged](../../preprocessor/managed-unmanaged.md)與[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 更正這個錯誤  
  
1.  移除無法編譯為 MSIL 之函式中的程式碼。  
  
2.  不要使用 **\/clr** 編譯模組，或將函式用 Unmanaged pragma 標示為 Unmanaged。  
  
## 範例  
 下列範例會產生 C2346。  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```