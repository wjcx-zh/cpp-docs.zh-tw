---
title: "編譯器錯誤 C2812 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2812"
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 不能使用 \/clr:pure 和 \/clr:safe 支援  
  
 因為 `#import` 需要使用原生編譯器支援程式庫，所以 [\#import 指示詞](../../preprocessor/hash-import-directive-cpp.md) 指示詞不能以 **\/clr:pure** 和 **\/clr:safe** 支援。  
  
## 範例  
 下列範例會產生 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```