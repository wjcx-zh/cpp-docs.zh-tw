---
title: "CManualAccessor::AddBindEntry | Microsoft Docs"
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
  - "ATL::CManualAccessor::AddBindEntry"
  - "ATL.CManualAccessor.AddBindEntry"
  - "CManualAccessor::AddBindEntry"
  - "AddBindEntry"
  - "CManualAccessor.AddBindEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddBindEntry 方法"
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor::AddBindEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將繫結項目加入輸出資料行。  
  
## 語法  
  
```  
  
      void AddBindEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL   
) throw ( );  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 欄編號。  
  
 `wType`  
 \[in\] 資料型別  
  
 `nColumnSize`  
 \[in\] 資料列大小 \(以位元組為單位\)。  
  
 `pData`  
 \[至緩衝區中的資料行之的指標。  
  
 `pLength`  
 \[out 欄位長度的指標，如果必須。  
  
 `pStatus`  
 \[in 要繫結之變數的指標的狀態，如果必須。  
  
## 備註  
 若要使用此功能，您必須先呼叫 [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。  要在 `CreateAccessor`中指定的欄位不能加入更多項目。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 範例](../../top/visual-cpp-samples.md)