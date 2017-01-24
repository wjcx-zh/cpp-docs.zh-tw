---
title: "CUtlProps::GetPropValue | Microsoft Docs"
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
  - "CUtlProps::GetPropValue"
  - "CUtlProps.GetPropValue"
  - "GetPropValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPropValue 方法"
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::GetPropValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從屬性集合取得屬性。  
  
## 語法  
  
```  
  
      OUT_OF_LINE HRESULT GetPropValue(  
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
 \[out\] 包含新屬性值的 VARIANT 的指標。  
  
## 傳回值  
 在發生失敗和 `S_OK` 的`Failure` ，如果成功。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)