---
title: "unchecked_uninitialized_copy | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_uninitialized_copy"
  - "unchecked_uninitialized_copy"
  - "std::unchecked_uninitialized_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_uninitialized_copy 函式"
ms.assetid: 38568841-314e-446b-91d0-92cc231e3b3c
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_uninitialized_copy
與 [uninitialized\_copy](../Topic/uninitialized_copy.md) 相同，但在定義 \_SECURE\_SCL\=1 時允許使用未檢查的迭代器做為輸出迭代器。 此函式定義於 [stdext 命名空間](../standard-library/stdext-namespace.md) 命名空間。  
  
> [!NOTE]
>  這個演算法是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。 使用這個演算法實作的程式碼不可移植。  
  
## 語法  
  
```  
template<class InputIterator, class ForwardIterator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest  
   );  
  
template<class InputIterator, class ForwardIterator, class Allocator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest,  
      Allocator& _Al  
   );  
```  
  
#### 參數  
 `_First`  
 輸入迭代器，為來源範圍中要複製的第一個項目定址。  
  
 `_Last`  
 輸入迭代器，為來源範圍中要複製的最後一個項目定址。  
  
 `_Dest`  
 正向迭代器，為目的範圍中要複製的第一個項目定址。  
  
 `_Al`  
 搭配這個物件使用的配置器類別。[vector::get\_allocator](../Topic/vector::get_allocator.md) 傳回物件的配置器類別。  
  
## 傳回值  
 正向迭代器，定址要接收複本之目的範圍中越過最後一個項目的位置。  
  
## 備註  
 請參閱 [uninitialized\_copy](../Topic/uninitialized_copy.md) 程式碼範例。  
  
 如需已檢查的迭代器的詳細資訊，請參閱 [已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間：**stdext