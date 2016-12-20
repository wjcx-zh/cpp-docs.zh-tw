---
title: "嚴重錯誤 C1104 | Microsoft Docs"
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
  - "C1104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1104"
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匯入 libid 時發生嚴重錯誤：'message'  
  
 編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 libid 來指定類型程式庫，同時又指定 `no_registry`。  
  
 如需詳細資訊，請參閱[\#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下列範例會產生 C1104：  
  
```  
// C1104.cpp #import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```