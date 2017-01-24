---
title: "編譯器錯誤 C3383 | Microsoft Docs"
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
  - "C3383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3383"
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/clr:safe 不支援 'operator new'  
  
 **\/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，並且不支援指標。  
  
 如需詳細資訊，請參閱：  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C\+\+ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## 範例  
 下列範例會產生 C3383。  
  
```  
// C3383.cpp // compile with: /clr:safe int main() { char* pCharArray = new char[256];  // C3383 }  
```