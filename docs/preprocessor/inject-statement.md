---
title: "inject_statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inject_statement"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "inject_statement 屬性"
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# inject_statement
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 將其做為來源文字的引數插入至類型程式庫標題。  
  
## 語法  
  
```  
inject_statement("source_text")  
```  
  
#### 參數  
 `source_text`  
 要插入至類型程式庫標題檔案的來源文字。  
  
## 備註  
 文字會放置在命名空間宣告的開頭位置，該命名空間宣告會在標題檔案中包裝類型程式庫內容。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)