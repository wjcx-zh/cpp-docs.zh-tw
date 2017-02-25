---
title: "CRowset::UpdateAll | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::UpdateAll"
  - "ATL.CRowset.UpdateAll"
  - "CRowset<TAccessor>.UpdateAll"
  - "ATL.CRowset<TAccessor>.UpdateAll"
  - "UpdateAll"
  - "CRowset.UpdateAll"
  - "ATL::CRowset<TAccessor>::UpdateAll"
  - "CRowset<TAccessor>::UpdateAll"
  - "ATL::CRowset::UpdateAll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UpdateAll 方法"
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::UpdateAll
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳送至這個對所有資料行，自上次擷取或 **Update** 呼叫所有暫止的變更。  
  
## 語法  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### 參數  
 `pcRows`  
 \[out `UpdateAll` 傳回行數就會嘗試更新位置的指標，如果必須。  
  
 `pphRow`  
 \[out `UpdateAll` 傳回資料列控制代碼它的記憶體的指標嘗試更新。  如果 `pphRow` 是空的，控制代碼不會傳回。  
  
 `ppStatus`  
 \[out **Update** 傳回資料列狀態值的位置的指標。  如果 `ppStatus` 是 null，則的狀態，則會傳回。  
  
## 備註  
 使用 [更新](../../data/oledb/crowset-update.md) 或，則為 `UpdateAll`，否則，因為這些行上次擷取或更新的傳輸進行的所有暫止變更的所有資料行。  `UpdateAll` 會更新已變更的每個資料列，不論您仍然有其控制代碼 \(請參閱 `pphRow`\)。  
  
 例如，在中，如果您在資料列集使用 **Insert** 插入五個資料行，您可以呼叫 **Update** 五次或一次呼叫 `UpdateAll` 更新它們。  
  
 這個方法要求選擇性介面 `IRowsetUpdate`，在所有提供者可能不支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  您也必須設定 **DBPROP\_IRowsetUpdate** 到 `VARIANT_TRUE` 在呼叫以包含資料列集的資料表的 **Open** 或命令。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)