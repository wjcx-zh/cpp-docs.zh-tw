---
title: "CManualAccessor::CreateParameterAccessor | Microsoft Docs"
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
  - "ATL::CManualAccessor::CreateParameterAccessor"
  - "ATL.CManualAccessor.CreateParameterAccessor"
  - "CManualAccessor.CreateParameterAccessor"
  - "CreateParameterAccessor"
  - "CManualAccessor::CreateParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateParameterAccessor 方法"
ms.assetid: d0a2095b-b37c-4472-accc-45ef365a18c8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor::CreateParameterAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

參數繫結配置記憶體結構並初始化參數資料成員。  
  
## 語法  
  
```  
  
      HRESULT CreateParameterAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### 參數  
 `nBindEntries`  
 \[的欄數。  
  
 `pBuffer`  
 \[in 儲存輸入資料行的緩衝區的指標。  
  
 `nBufferSize`  
 \[緩衝區的大小 \(以位元組為單位\)。  
  
## 傳回值  
 其中一個 `HRESULT` 值。  
  
## 備註  
 您必須在呼叫 [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)之前呼叫這個函式。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)   
 [CManualAccessor::AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)