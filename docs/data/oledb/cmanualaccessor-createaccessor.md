---
title: "CManualAccessor::CreateAccessor | Microsoft Docs"
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
  - "ATL::CManualAccessor::CreateAccessor"
  - "CreateAccessor"
  - "ATL.CManualAccessor.CreateAccessor"
  - "CManualAccessor.CreateAccessor"
  - "CManualAccessor::CreateAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateAccessor 方法"
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor::CreateAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

資料繫結配置記憶體結構和初始化的資料成員。  
  
## 語法  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### 參數  
 `nBindEntries`  
 \[in\] 資料行的數目。  這個數目應該符合呼叫數加上 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) 函式。  
  
 `pBuffer`  
 \[in\] 儲存輸出行的緩衝區的指標。  
  
 `nBufferSize`  
 \[in\] 緩衝區的大小 \(以位元組為單位\)。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 在呼叫 `CManualAccessor::AddBindEntry` 函式之前，呼叫這個函式。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 範例](../../top/visual-cpp-samples.md)