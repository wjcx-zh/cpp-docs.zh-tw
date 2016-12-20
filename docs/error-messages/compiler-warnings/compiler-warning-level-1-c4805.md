---
title: "編譯器警告 (層級 1) C4805 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4805"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4805"
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4805
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation'：作業中不安全的混用類型 'type' 和類型 'type'  
  
 進行 [bool](../../cpp/bool-cpp.md) 和 [int](../../c-language/integer-types.md) 之間的比較作業時會產生此警告。 下列範例會產生 C4805：  
  
```  
// C4805.cpp // compile with: /W1 int main() { int i = 1; bool b = true; if (i == b) {   // C4805, comparing bool and int variables } }  
```