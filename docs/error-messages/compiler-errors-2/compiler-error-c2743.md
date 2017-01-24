---
title: "編譯器錯誤 C2743 | Microsoft Docs"
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
  - "C2743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2743"
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 無法以 \_\_clrcall 解構函式或複製建構函式攔截原生型別  
  
 使用 **\/clr** \(而不是 **\/clr:pure**\) 編譯的模組試圖攔截原生型別的例外狀況，而其中該型別的解構函式或複製建構函式使用的是 \_`_clrcall` 呼叫慣例。  
  
 使用 **\/clr** \(而不是 **\/clr:pure**\) 進行編譯時，例外狀況處理 \(Exception Handling\) 預期原生型別中的成員函式為 [\_\_cdecl](../../cpp/cdecl.md) 而不是 [\_\_clrcall](../../cpp/clrcall.md)。  有使用 `__clrcall` 呼叫慣例之成員函式的原生型別無法在使用 **\/clr** 編譯的模組中攔截。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 下列範例會產生 C2743。  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```