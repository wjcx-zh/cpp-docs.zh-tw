---
title: "編譯器警告 (層級 4) C4937 | Microsoft Docs"
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
  - "C4937"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4937"
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4937
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

難以辨別 'text1' 和 'text2' 是否為 'directive' 的引數  
  
 因為編譯器處理指示詞引數的方式，無法辨別對編譯器有意義的名稱，例如有多種文字涵義的關鍵字 \(單和雙底線格式\)。  
  
 這類字串的範例如 \_\_cdecl 和 \_\_forceinline。  請注意，\/Za 中只會啟用雙底線格式。  
  
 下列範例會產生 C4937：  
  
```  
// C4937.cpp // compile with: /openmp /W4 #include "omp.h" int main() { #pragma omp critical ( __leave )   // C4937 ; // OK #pragma omp critical ( leave ) ; }  
```