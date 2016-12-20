---
title: "嚴重錯誤 C1103 | Microsoft Docs"
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
  - "C1103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1103"
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匯入 progid 時發生嚴重錯誤: 'message'  
  
 編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 progid 來指定類型程式庫，同時又指定 `no_registry`。  
  
 如需詳細資訊，請參閱[\#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下列範例會產生 C1103：  
  
```  
// C1103.cpp #import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```