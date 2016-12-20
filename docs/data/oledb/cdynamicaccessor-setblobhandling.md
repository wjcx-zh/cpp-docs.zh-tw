---
title: "CDynamicAccessor::SetBlobHandling | Microsoft Docs"
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
  - "CDynamicAccessor::SetBlobHandling"
  - "CDynamicAccessor.SetBlobHandling"
  - "ATL::CDynamicAccessor::SetBlobHandling"
  - "SetBlobHandling"
  - "ATL.CDynamicAccessor.SetBlobHandling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobHandling 方法"
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetBlobHandling
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定處理目前行的 BLOB 值。  
  
## 語法  
  
```  
  
      bool SetBlobHandling(  
   DBBLOBHANDLINGENUM eBlobHandling   
);  
```  
  
#### 參數  
 `eBlobHandling`  
 指定 BLOB 資料的方式處理。  它可以接受下列值:  
  
-   **DBBLOBHANDLING\_DEFAULT**:大於 `nBlobSize` 管理的資料 \( `SetBlobSizeLimit`集合\) 做為 BLOB 資料並透過 `ISequentialStream` 或 `IStream` 物件擷取它。  這個選項大於 `nBlobSize` 會嘗試繫結至包含資料的每個資料行或清單做為 **DBTYPE\_IUNKNOWN** 當 BLOB 資料。  
  
-   **DBBLOBHANDLING\_NOSTREAMS**:大於 `nBlobSize` 管理的資料 \( `SetBlobSizeLimit`集合\) 做為 BLOB 資料並在提供者配置，消費者擁有記憶體的參考擷取它。  這個選項為有一個以上的 BLOB 資料行的資料表是有用的，因此，提供者只支援每個存取子的 `ISequentialStream` 物件。  
  
-   **DBBLOBHANDLING\_SKIP**:略過 \(不繫結\) 限定為包含的資料 BLOB \(存取子不會繫結也不會擷取資料行值，但會擷取資料列狀態和長度\)。  
  
## 備註  
 您應該在呼叫 **Open**前呼叫 `SetBlobHandling` 。  
  
 建構函式方法 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 設定處理值的 BLOB 對 **DBBLOBHANDLING\_DEFAULT**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)