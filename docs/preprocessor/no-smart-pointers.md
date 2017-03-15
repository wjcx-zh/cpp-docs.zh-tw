---
title: "no_smart_pointers | Microsoft Docs"
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
  - "no_search_pointers"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_smart_pointers 屬性"
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_smart_pointers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 不為類型程式庫中的所有介面建立智慧型指標。  
  
## 語法  
  
```  
no_smart_pointers  
```  
  
## 備註  
 根據預設，當您使用 `#import` 時，會得到類型程式庫中所有介面的智慧型指標宣告。  這些智慧型指標的類型是 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)