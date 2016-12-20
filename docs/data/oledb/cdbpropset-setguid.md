---
title: "CDBPropSet::SetGUID | Microsoft Docs"
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
  - "ATL.CDBPropSet.SetGUID"
  - "CDBPropSet.SetGUID"
  - "ATL::CDBPropSet::SetGUID"
  - "SetGUID"
  - "CDBPropSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty 方法"
  - "SetGUID 方法"
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 **DBPROPSET** 結構的 **guidPropertySet** 欄位。  
  
## 語法  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### 參數  
 `guid`  
 \[in\] GUID 用來設定 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構的 **guidPropertySet** 欄位。  
  
## 備註  
 這個欄位可以由 [建構函式](../../data/oledb/cdbpropset-cdbpropset.md) 設定。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBPropSet 類別](../../data/oledb/cdbpropset-class.md)