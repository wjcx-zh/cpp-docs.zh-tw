---
title: "CManualAccessor::AddParameterEntry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CManualAccessor::AddParameterEntry"
  - "ATL.CManualAccessor.AddParameterEntry"
  - "CManualAccessor.AddParameterEntry"
  - "AddParameterEntry"
  - "ATL::CManualAccessor::AddParameterEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddParameterEntry 方法"
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CManualAccessor::AddParameterEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將參數輸入到參數輸入結構。  
  
## 語法  
  
```  
  
      void AddParameterEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT   
) throw ( );  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\]參數的數目。  
  
 `wType`  
 \[in\] 資料型別  
  
 `nColumnSize`  
 \[in\] 資料列大小 \(以位元組為單位\)。  
  
 `pData`  
 \[in\] 至緩衝區中的資料行之的指標。  
  
 `pLength`  
 \[in\] 欄位長度的指標，如果必須。  
  
 `pStatus`  
 \[in\] 要繫結之變數的指標的狀態，如果必須。  
  
 *eParamIO*  
 \[in\]指定繫結是相關的參數是否為輸入、輸出入或輸出參數。  
  
## 備註  
 若要使用此功能，您必須先呼叫 [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [DBViewer 範例](../../top/visual-cpp-samples.md)