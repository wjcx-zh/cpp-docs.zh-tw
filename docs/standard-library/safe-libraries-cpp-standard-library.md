---
title: "安全程式庫：C++ 標準程式庫 | Microsoft Docs"
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
  - "_SCL_SECURE_NO_DEPRECATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "安全程式庫"
  - "安全程式庫, Standard C++ 程式庫"
  - "安全 Standard C++ 程式庫"
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 安全程式庫：C++ 標準程式庫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 隨附的程式庫 \(包括 Standard C\+\+ 程式庫\) 已做了數項改進，因此更安全。  
  
 Standard C\+\+ 程式庫中的幾個方法已知可能不安全，因為這些方法可能會導致緩衝區溢位或其他程式碼缺失。 建議您不要使用這些方法，目前已建立更安全的新方法來取代這些方法。 這些新方法的結尾全部都是 `_s`。  
  
 迭代器和演算法也已做了數項改進，因此更安全。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)、[偵錯迭代器支援](../standard-library/debug-iterator-support.md)和 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 備註  
 下表列出可能不安全的 Standard C\+\+ 程式庫方法，以及更安全的對等項目：  
  
|可能不安全的方法|更安全的對等項目|  
|--------------|--------------|  
|[basic\_string::copy](../Topic/basic_string::copy.md)|[basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md)|  
|[char\_traits::copy](../Topic/char_traits::copy.md)|[char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md)|  
  
 如果您呼叫上述任何一個可能不安全的方法，或不當使用迭代器，編譯器會產生[編譯器警告 \(層級 3\) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 如需如何停用這些警告的相關資訊，請參閱 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## 本節內容  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)  
  
 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)  
  
 [已檢查的迭代器](../standard-library/checked-iterators.md)  
  
 [偵錯迭代器支援](../standard-library/debug-iterator-support.md)  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)