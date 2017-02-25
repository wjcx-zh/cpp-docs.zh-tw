---
title: "ATL 集合和列舉程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合介面"
  - "集合, ATL 類別"
  - "列舉程式介面"
  - "列舉程式, ATL 類別"
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ATL 集合和列舉程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`collection` 是提供介面允許存取資料項目的 COM 物件 \(未經處理資料或其他物件\) 的存取。  根據提供的存取準則對於物件的介面稱為 *集合介面*。  
  
 最起碼，集合介面必須提供傳回此集合中的項目數、 **項目** 屬性會根據項目根據索引值和 `_NewEnum` 屬性的傳回集合的列舉值的 **計數** 屬性。  選項性的，設定介面可提供 **新增** 和 **移除** 方法可將項目插入至集合或從集合刪除和 **清除** 方法移除所有項目。  
  
 `enumerator` 是逐一查看提供介面傳遞集合中的項目的 COM 物件。  列舉值介面傳遞四個需要的方法提供序列存取集合的項目: `Next`、 **略過**、 **重設**和 `Clone`。  
  
 您可以閱讀進一步了解列舉值介面原始模型 \(但完全假想\)  [IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx) 介面。  
  
## 本章節內容  
 [ATL 集合和列舉值類別](../atl/atl-collection-and-enumerator-classes.md)  
 簡要說明並提供協助您實作集合和列舉值的 ATL 類別。  
  
 [集合和列舉值之介面的設計原則](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 討論在介面之後的每種不同的設計原則。  
  
 [實作以 STL 集合](../atl/implementing-an-stl-based-collection.md)  
 透過標準樣板程式庫中建立 \(STL\) 架構集合的實作的擴充的範例。  
  
## 相關章節  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用 Active Template Library，提供概念性主題連結說明如何撰寫程式。  
  
 [ATLCollections 範例](../top/visual-cpp-samples.md)  
 示範使用 `ICollectionOnSTLImpl` 和 `CComEnumOnSTL`的範例和自訂複製原則類別的實作。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)