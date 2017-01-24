---
title: "CRowset::MoveToBookmark | Microsoft Docs"
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
  - "ATL::CRowset::MoveToBookmark"
  - "ATL::CRowset<TAccessor>::MoveToBookmark"
  - "ATL.CRowset.MoveToBookmark"
  - "ATL.CRowset<TAccessor>.MoveToBookmark"
  - "MoveToBookmark"
  - "CRowset::MoveToBookmark"
  - "CRowset.MoveToBookmark"
  - "CRowset<TAccessor>::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark 方法"
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取書籤指示資料列或資料行中的指定位移 \(`lSkip`\) 從該書籤。  
  
## 語法  
  
```  
  
      HRESULT MoveToBookmark(   
   const CBookmarkBase& bookmark,   
   LONG lSkip = 0    
) throw( );  
```  
  
#### 參數  
 `bookmark`  
 \[表示您要擷取資料之位置的書籤。  
  
 `lSkip`  
 \[數字計數從書籤的行到目標行。  如果 `lSkip` 是零，將擷取的第一行是書籤的行。  如果 `lSkip` 為 1，將擷取的第一個資料行是資料行在書籤的資料列之後。  如果 `lSkip` 為 \-1，將擷取的第一個資料行是資料行在書籤的資料列之前。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性 `IRowsetLocate` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  您也必須設定為 `VARIANT_TRUE` **DBPROP\_IRowsetLocate** 和 **DBPROP\_CANFETCHBACKWARDS** 集合至 `VARIANT_TRUE` 在呼叫以包含資料列集的資料表的 **Open** 或命令。  
  
 如需使用對消費者使用書籤的資訊，請參閱 [使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)