---
title: "IRowsetImpl::CreateRow | Microsoft Docs"
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
  - "IRowsetImpl.CreateRow"
  - "ATL.IRowsetImpl.CreateRow"
  - "ATL::IRowsetImpl::CreateRow"
  - "CreateRow"
  - "IRowsetImpl::CreateRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRow 方法"
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::CreateRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 呼叫的 Helper 方法會配置新的 **HROW**。  
  
## 語法  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
```  
  
#### 參數  
 *lRowsOffset*  
 建立資料行的游標位置。  
  
 *cRowsObtained*  
 傳遞回使用者的參考表示建立的資料列數目。  
  
 *rgRows*  
 陣列 **HROW**傳回至具有新建立的資料列控制代碼的呼叫端。  
  
## 備註  
 如果資料行存在，這個方法會呼叫 [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) 並傳回。  否則，它會配置新的 RowClass 範本變數執行個體並將它加入至 [m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)