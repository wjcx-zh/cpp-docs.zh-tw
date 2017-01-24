---
title: "_HAS_ITERATOR_DEBUGGING | Microsoft Docs"
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
  - "_HAS_ITERATOR_DEBUGGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_HAS_ITERATOR_DEBUGGING"
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: 7
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _HAS_ITERATOR_DEBUGGING
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 Iterator 偵錯功能是否在偵錯組建啟用。  根據預設， Iterator 偵錯已啟用。  如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制項的 `_HAS_ITERATOR_DEBUGGING`。  如需詳細資訊，請參閱[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 備註  
 若要啟用 Iterator Debug 組建，並將 **\_HAS\_ITERATOR\_DEBUGGING** 設為 1:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 1  
```  
  
 **\_HAS\_ITERATOR\_DEBUGGING** 無法設定為 1 在正式版本組建。  
  
 若要停用 Iterator Debug 組建，並將 **\_HAS\_ITERATOR\_DEBUGGING** 設為 0:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 0  
```  
  
## 請參閱  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
 [已檢查的迭代器](../standard-library/checked-iterators.md)   
 [安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)