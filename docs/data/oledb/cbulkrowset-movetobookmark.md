---
title: "CBulkRowset::MoveToBookmark | Microsoft Docs"
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
  - "CBulkRowset<TAccessor>::MoveToBookmark"
  - "CBulkRowset.MoveToBookmark"
  - "MoveToBookmark"
  - "ATL.CBulkRowset.MoveToBookmark"
  - "CBulkRowset::MoveToBookmark"
  - "ATL::CBulkRowset<TAccessor>::MoveToBookmark"
  - "ATL::CBulkRowset::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark 方法"
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取書籤指示資料列或資料行中的指定位移 \(`lSkip`\) 從該書籤。  
  
## 語法  
  
```  
  
      HRESULT MoveToBookmark(  
   const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0   
) throw( );  
```  
  
#### 參數  
 `bookmark`  
 \[表示您要擷取資料之位置的書籤。  
  
 `lSkip`  
 \[數字計數從書籤的行到目標行。  如果 `lSkip` 是零，將擷取的第一行是書籤的行。  如果 `lSkip` 為 1，將擷取的第一個資料行是資料行在書籤的資料列之後。  如果 `lSkip` 為 \-1，將擷取的第一個資料行是資料行在書籤的資料列之前。  
  
## 傳回值  
 請參閱 *OLE DB 程式設計人員參考*中的[oledbirowset\_\_getdata](https://msdn.microsoft.com/en-us/library/ms716988.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)