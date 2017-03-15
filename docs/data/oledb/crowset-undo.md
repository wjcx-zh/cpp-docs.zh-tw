---
title: "CRowset::Undo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset.Undo"
  - "ATL::CRowset<TAccessor>::Undo"
  - "CRowset<TAccessor>::Undo"
  - "ATL.CRowset.Undo"
  - "ATL.CRowset<TAccessor>.Undo"
  - "CRowset<TAccessor>.Undo"
  - "ATL::CRowset::Undo"
  - "CRowset::Undo"
  - "Undo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Undo 方法"
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::Undo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自上次擷取或 [更新](../../data/oledb/crowset-update.md) 移除所做的任何變更。  
  
## 語法  
  
```  
  
      HRESULT Undo(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### 參數  
 `pcRows`  
 \[out\] **Undo** 傳回資料列數其位置的指標嘗試如果必須取消。  
  
 `phRow`  
 \[out\] **Undo** 傳回陣列的控制代碼所有資料列其位置之指標嘗試如果必須取消。  
  
 `pStatus`  
 \[out\] **Undo** 傳回資料列狀態值的位置的指標。  如果 `pStatus` 是 null，則無狀態傳回。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性 `IRowsetUpdate` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetUpdate** 到 `VARIANT_TRUE`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)