---
title: "IColumnsInfoImpl 類別 | Microsoft Docs"
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
  - "ATL.IColumnsInfoImpl<T>"
  - "ATL::IColumnsInfoImpl"
  - "IColumnsInfoImpl"
  - "ATL.IColumnsInfoImpl"
  - "ATL::IColumnsInfoImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IColumnsInfoImpl 類別"
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IColumnsInfoImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IColumnsInfoImpl`。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)|傳回大部分消費者所需的資料行中繼資料。|  
|[MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)|傳回資料列集中指定之資料行 ID 所識別資料行的序數陣列。|  
  
## 備註  
 在資料列集和命令的強制介面。  若要修改您的提供者的 `IColumnsInfo` 實作行為，您必須修改提供者資料行對應。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)