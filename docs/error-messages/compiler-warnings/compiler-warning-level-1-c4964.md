---
title: "編譯器警告 (層級 1) C4964 | Microsoft Docs"
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
  - "C4964"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4964"
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4964
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未指定最佳化選項，將不會收集內部分析  
  
 [\/GL](../../build/reference/gl-whole-program-optimization.md) 和 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 都已指定，但並未要求任何最佳化，所以將不會產生任何 .pgc 檔案，因此也不可能進行任何特性指引最佳化。  
  
 如果不要在執行應用程式時產生 .pgc 檔，請指定 [\/O](../../build/reference/o-options-optimize-code.md) 其中一個編譯器選項。  
  
 下列範例會產生 C4964：  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```