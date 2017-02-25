---
title: "&lt;ccomplex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<ccomplex>"
dev_langs: 
  - "C++"
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;ccomplex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包括 STL 標頭 [\<complex\>](../standard-library/complex.md)，它會有效率地包括標準 C 程式庫標頭 \<complex.h\>，並將相關聯的名稱加入至 `std` 命名空間。  
  
## 語法  
  
```cpp  
  
#include <ccomplex>  
  
```  
  
## 備註  
 包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。  
  
 名稱 `clog` \(宣告於 \<complex.h\> 中\) 未定義在 `std` 命名空間中，因為可能發生與 `clog` \(宣告於 [\<iostream\>](../standard-library/iostream.md) 中\) 的衝突。  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)