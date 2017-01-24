---
title: "CDBPropIDSet::CDBPropIDSet | Microsoft Docs"
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
  - "ATL::CDBPropIDSet::CDBPropIDSet"
  - "CDBPropIDSet"
  - "CDBPropIDSet.CDBPropIDSet"
  - "CDBPropIDSet::CDBPropIDSet"
  - "ATL.CDBPropIDSet.CDBPropIDSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropIDSet 類別, 建構函式"
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet::CDBPropIDSet
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建構函式。  初始化 **rgProperties**和 **cProperties**和 \(選擇性\) [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 結構的 **guidPropertySet** 欄位。  
  
## 語法  
  
```  
  
      CDBPropIDSet(  
   const GUID& guid   
);  
CDBPropIDSet(   
   const CDBPropIDSet& propidset    
);  
CDBPropIDSet( );  
```  
  
#### 參數  
 `guid`  
 \[\] GUID 用來用來初始化 **guidPropertySet** 欄位。  
  
 *propidset*  
 \[複製建構的另一個 `CDBPropIDSet` 物件。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)