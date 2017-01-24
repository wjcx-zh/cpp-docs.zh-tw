---
title: "_SECURE_SCL | Microsoft Docs"
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
  - "_SECURE_SCL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SECURE_SCL"
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _SECURE_SCL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 [已檢查的迭代器](../standard-library/checked-iterators.md) 是否已啟用。  如果已定義為 1，不安全的 Iterator 使用會導致執行階段錯誤，而且程式結束。  如果已定義為 0，已檢查的 Iterator 停用。  在偵錯模式， **\_SECURE\_SCL** 的預設值為 1，表示已檢查的 Iterator 已啟用。  在發行模式下， `_SECURE_SCL` 的預設值為 0。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制項的 `_SECURE_SCL`。  如需詳細資訊，請參閱[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 備註  
 若要啟用已檢查的 Iterator，請將 **\_SECURE\_SCL** 設為 1:  
  
```  
#define _SECURE_SCL 1  
```  
  
 若要停用已檢查的 Iterator，請將 **\_SECURE\_SCL** 設為 0:  
  
```  
#define _SECURE_SCL 0  
```  
  
 如需如何停用有關已檢查的 Iterator 的警告的詳細資訊，請參閱 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## 請參閱  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [已檢查的迭代器](../standard-library/checked-iterators.md)   
 [偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
 [安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)