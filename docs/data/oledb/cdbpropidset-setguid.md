---
title: "CDBPropIDSet::SetGUID | Microsoft Docs"
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
  - "CDBPropIDSet.SetGUID"
  - "ATL::CDBPropIDSet::SetGUID"
  - "SetGUID"
  - "ATL.CDBPropIDSet.SetGUID"
  - "CDBPropIDSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetGUID 方法"
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 **DBPROPIDSET** 結構的 GUID 欄位。  
  
## 語法  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### 參數  
 `guid`  
 \[in\] GUID 用來設定 [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 結構的 **guidPropertySet** 欄位。  
  
## 備註  
 這個欄位可以由 [建構函式](../../data/oledb/cdbpropidset-cdbpropidset.md) 設定。  呼叫此函式則為這個類別會使用預設建構函式。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)