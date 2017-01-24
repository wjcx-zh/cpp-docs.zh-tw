---
title: "CUtlProps::SetPropValue | Microsoft Docs"
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
  - "SetPropValue"
  - "ATL::CUtlProps<T>::SetPropValue"
  - "ATL.CUtlProps<T>.SetPropValue"
  - "ATL.CUtlProps.SetPropValue"
  - "CUtlProps::SetPropValue"
  - "CUtlProps<T>::SetPropValue"
  - "CUtlProps.SetPropValue"
  - "CUtlProps<T>.SetPropValue"
  - "ATL::CUtlProps::SetPropValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetPropValue 方法"
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::SetPropValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定屬性集合的屬性。  
  
## 語法  
  
```  
  
      HRESULT SetPropValue(  
   const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue   
);  
```  
  
#### 參數  
 `pguidPropSet`  
 \[in\] PropSet 的 GUID。  
  
 `dwPropId`  
 \[in\] 屬性索引。  
  
 `pvValue`  
 \[in\] 包含新屬性值的 VARIANT 的指標。  
  
## 傳回值  
 在失敗時是`Failure`，如果成功則是`S_OK`。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)