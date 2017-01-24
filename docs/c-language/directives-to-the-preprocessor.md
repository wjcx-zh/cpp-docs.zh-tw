---
title: "前置處理器的指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 前置處理器的指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「指示詞」會指示 C 前置處理器在編譯之前，於程式文字上執行特定動作。  [前置處理器指示詞](../preprocessor/preprocessor-directives.md)將在《前置處理器參考》中完整說明。  這個範例會使用前置處理器指示詞 `#define`：  
  
```  
#define MAX 100  
```  
  
 這個陳述式會指示編譯器在編譯前，將出現 `MAX` 的每一個位置取代為 `100`。  C 編譯器前置處理器指示詞包括：  
  
|\#define|\#endif|\#ifdef|\#line|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|**\#ifndef**|**\#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## 請參閱  
 [原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)