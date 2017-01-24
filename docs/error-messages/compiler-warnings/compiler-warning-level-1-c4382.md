---
title: "編譯器警告 (層級 1) C4382 | Microsoft Docs"
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
  - "C4382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4382"
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擲回 'type' : 具有 \_\_clrcall 解構函式或複製建構函式的型別，只能在 \/clr:pure 模組中攔截  
  
 使用 **\/clr** \(而不是 **\/clr:pure**\) 進行編譯時，例外狀況處理 \(Exception Handling\) 預期原生型別中的成員函式為 [\_\_cdecl](../../cpp/cdecl.md) 而不是 [\_\_clrcall](../../cpp/clrcall.md)。  有使用 `__clrcall` 呼叫慣例之成員函式的原生型別無法在使用 **\/clr** 編譯的模組中攔截。  
  
 如果例外狀況將在使用 **\/clr:pure** 編譯的模組中攔截，您可以忽略這項警告。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 下列範例會產生 C4382。  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```