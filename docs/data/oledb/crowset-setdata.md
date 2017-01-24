---
title: "CRowset::SetData | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>.SetData"
  - "SetData"
  - "ATL::CRowset::SetData"
  - "CRowset<TAccessor>.SetData"
  - "CRowset::SetData"
  - "ATL.CRowset.SetData"
  - "CRowset.SetData"
  - "CRowset<TAccessor>::SetData"
  - "ATL::CRowset<TAccessor>::SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData 方法"
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在資料列的一個或多個資料行中設定資料值。  
  
## 語法  
  
```  
  
      HRESULT SetData( ) const throw( );   
HRESULT SetData(  
   int nAccessor   
) const throw( );  
```  
  
#### 參數  
 `nAccessor`  
 \[in\]使用存取子的數字為存取資料。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 對於不接受引數的 `SetData` 表單，所有存取子用來更新。  您通常會呼叫 **SetData** 設定資料行中的資料值，然後呼叫 [更新](../../data/oledb/crowset-update.md) 傳輸這些變更。  
  
 這個方法要求選擇性 `IRowsetChange` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetChange** 到 `VARIANT_TRUE`。  
  
 如果第一個或更多資料列不可寫入，設定作業可能會失敗。  請修改您的資料指標 \(Cursor\) 對應以修正這個問題。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)