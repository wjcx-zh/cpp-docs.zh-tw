---
title: "編譯器錯誤 C3295 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3295"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3295"
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 編譯器錯誤 C3295
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#pragma pragma' 只能使用在全域或命名空間範圍  
  
 有些 pragma 無法用於函式中。  如需詳細資訊，請參閱 [Pragma 指示詞和 \_\_Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
## 範例  
 下列範例會產生 C3295。  
  
```  
// C3295.cpp int main() { #pragma managed   // C3295 }  
```