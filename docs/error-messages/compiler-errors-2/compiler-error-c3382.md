---
title: "編譯器錯誤 C3382 | Microsoft Docs"
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
  - "C3382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3382"
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/clr:safe 不支援 'sizeof'  
  
 **\/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，而且不支援 sizeof，因為 sizeof 運算子的傳回值是 size\_t，其大小視作業系統而異。  
  
 如需詳細資訊，請參閱：  
  
-   [sizeof 運算子](../../cpp/sizeof-operator.md)  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C\+\+ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## 範例  
 下列範例會產生 C3382。  
  
```  
// C3382.cpp // compile with: /clr:safe int main() { sizeof( char );   // C3382 }  
```