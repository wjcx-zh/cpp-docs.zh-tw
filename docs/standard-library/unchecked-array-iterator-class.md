---
title: "unchecked_array_iterator 類別 | Microsoft Docs"
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
  - "unchecked_array_iterator"
  - "stdext::unchecked_array_iterator"
dev_langs: 
  - "C++"
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unchecked_array_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`unchecked_array_iterator` 類別可讓您將陣列或指標包裝在未檢查的迭代器中。  使用這個類別做為原始指標或陣列的包裝函式 \(使用 [make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md) 函式\)，做為管理未檢查指標警告的目標方式，而非全域的關閉這些警告訊息。  如果可能，請優先使用這個類別的已檢查版本 [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)。  
  
> [!NOTE]
>  這個類別是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。  
  
## 語法  
  
```  
template <class Iterator>  
    class unchecked_array_iterator;  
```  
  
## 備註  
 這個類別是在 [stdext](../standard-library/stdext-namespace.md) 命名空間中定義的。  
  
 這是 [checked\_array\_iterator 類別](../standard-library/checked-array-iterator-class.md)的未檢查版本並支援所有相同的多載和成員。  如需已檢查的迭代器功能的詳細資訊和程式碼範例，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)