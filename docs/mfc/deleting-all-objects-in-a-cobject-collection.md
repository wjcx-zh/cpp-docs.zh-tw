---
title: "刪除 CObject 集合中的所有物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 類別集合"
  - "CObject 類別, 在集合中刪除"
  - "集合類別, 刪除所有物件"
  - "集合類別, 共用物件"
  - "物件 [C++], 在集合中刪除"
  - "CObject 集合中的物件"
  - "CObject 集合中的物件, 刪除"
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 刪除 CObject 集合中的所有物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何刪除集合中的所有物件 \(不需刪除集合物件\)。  
  
 要移除的 `CObject`集合的所有物件 \(衍生自 `CObject`的或物件\)，請使用本文所述的其中一個反覆運算技術 [存取集合的所有成員。](../mfc/accessing-all-members-of-a-collection.md) 依次刪除每一個物件。  
  
> [!CAUTION]
>  集合中的物件可以共用。  也就是集合中保留物件指標，不過，程式的其他部分可能也有指標到同一物件。  您必須小心刪除使用物件，共用的物件，直到所有部分完成。  
  
 本文說明如何刪除物件在:  
  
-   [一個清單。](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [陣列](#_core_to_delete_all_elements_in_an_array)  
  
-   [對應](#_core_to_delete_all_elements_in_a_map)  
  
#### 刪除在指標清單中的所有物件至 CObject  
  
1.  使用 `GetHeadPosition` 和 `GetNext` 逐一查看清單。  
  
2.  使用 **delete** 運算子刪除每一個物件，它在反覆運算時。  
  
3.  在物件與這些項目刪除後，請呼叫 `RemoveAll` 函式從清單移除所有項目。  
  
 下列範例顯示如何從 `CPerson` 刪除物件清單中的所有物件。  在清單中的每個物件是指向堆積最初所配置的 `CPerson` 物件。  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 最後一個函式呼叫，則為 `RemoveAll`，是從清單移除所有項目的清單成員函式。  成員函式 `RemoveAt` 移除單一項目。  
  
 請注意在刪除項目的物件並移除項目之間的差異。  移除項目從清單只會取消對物件的參考。  物件仍然存在於記憶體中。  當您刪除物件時，它會停止存在，而且它的記憶體回收。  因此，移除項目很重要，在項目的物件刪除之後，讓清單不會嘗試存取不存在的物件。  
  
#### 刪除陣列中的所有項目  
  
1.  使用 `GetSize` 和整數索引值逐一查看陣列。  
  
2.  當它在反覆運算時，使用 **delete** 運算子刪除每一個項目。  
  
3.  在刪除之後，請呼叫 `RemoveAll` 函式可從陣列移除所有項目。  
  
     刪除陣列中所有的項目程式碼如下所示:  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 與上面的範例清單，您可以呼叫 `RemoveAll` 移除陣列或 `RemoveAt` 的所有項目移除個別項目。  
  
#### 刪除對應中的所有項目  
  
1.  使用 `GetStartPosition` 和 `GetNextAssoc` 逐一查看陣列。  
  
2.  使用 **delete** 運算子刪除索引鍵和值每個對應項目的，它在反覆運算時。  
  
3.  在刪除之後，請呼叫 `RemoveAll` 函式可從對應移除所有項目。  
  
     要刪除之 `CMap` 集合中所有項目的程式碼如下。  對應中的每個項目都具有字串做為索引鍵和 `CPerson` 物件 \(衍生自 `CObject`\) 做為值。  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 您可以呼叫 `RemoveAll` 移除對應或 `RemoveKey` 的所有項目移除個別元素具有指定索引鍵的。  
  
## 請參閱  
 [存取集合的所有成員](../mfc/accessing-all-members-of-a-collection.md)