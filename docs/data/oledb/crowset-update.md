---
title: "CRowset::Update | Microsoft Docs"
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
  - "CRowset.Update"
  - "ATL.CRowset.Update"
  - "ATL.CRowset<TAccessor>.Update"
  - "ATL::CRowset<TAccessor>::Update"
  - "CRowset<TAccessor>::Update"
  - "CRowset::Update"
  - "CRowset<TAccessor>.Update"
  - "ATL::CRowset::Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update 方法"
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳送至這個對目前資料列，自上次擷取或 **Update** 呼叫所有暫止的變更。  
  
## 語法  
  
```  
  
      HRESULT Update(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### 參數  
 `pcRows`  
 \[out **Update** 傳回行數就會嘗試更新位置的指標，如果必須。  
  
 `phRow`  
 \[out **Update** 傳回資料列控制代碼其位置的指標嘗試更新。  如果 `phRow` 是空的，控制代碼不會傳回。  
  
 `pStatus`  
 \[out **Update** 傳回資料列狀態值的位置的指標。  如果 `pStatus` 是 null，則的狀態，則會傳回。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 傳輸即完成所有暫止的變更對目前資料列上次擷取或更新的 \(使用 **Update** 或 [UpdateAll](../../data/oledb/crowset-updateall.md)\)。  您通常會呼叫 [SetData](../../data/oledb/crowset-setdata.md) 會設定資料行中的資料值，然後呼叫 **Update** 傳輸這些變更。  
  
 這個方法要求選擇性介面 `IRowsetUpdate`，在所有提供者可能不支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  您也必須設定 **DBPROP\_IRowsetUpdate** 到 `VARIANT_TRUE` 在呼叫以包含資料列集的資料表的 **Open** 或命令。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)