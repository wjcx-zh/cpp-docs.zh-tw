---
title: "CRowset::GetApproximatePosition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset::GetApproximatePosition"
  - "ATL::CRowset<TAccessor>::GetApproximatePosition"
  - "CRowset.GetApproximatePosition"
  - "CRowset::GetApproximatePosition"
  - "GetApproximatePosition"
  - "ATL.CRowset.GetApproximatePosition"
  - "CRowset<TAccessor>::GetApproximatePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetApproximatePosition 方法"
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetApproximatePosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回與書籤對應的資料列的大約位置。  
  
## 語法  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### 參數  
 `pBookmark`  
 識別資料行要找到之位置的書籤的指標。  **NULL** ，如果只需要資料行計數。  
  
 *P位置*  
 \[out `GetApproximatePosition` 傳回資料列其位置之位置的指標。  **NULL** ，如果不需要位置。  
  
 `pcRows`  
 out `GetApproximatePosition` 傳回資料列總數的位置的指標。  **NULL** ，如果不需要資料行計數。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性 `IRowsetScroll` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetScroll** 到 `VARIANT_TRUE`。  
  
 如需使用對消費者使用書籤的資訊，請參閱 [使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)