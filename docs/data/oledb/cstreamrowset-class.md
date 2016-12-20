---
title: "CStreamRowset 類別 | Microsoft Docs"
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
  - "ATL::CStreamRowset<TAccessor>"
  - "ATL::CStreamRowset"
  - "CStreamRowset"
  - "ATL.CStreamRowset<TAccessor>"
  - "ATL.CStreamRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStreamRowset 類別"
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStreamRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 `CCommand` 或 `CTable` 宣告。  
  
## 語法  
  
```  
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|建構函式。  執行個體化及初始化 `CStreamRowset` 物件。|  
|[關閉](../../data/oledb/cstreamrowset-close.md)|釋放類別中的 [ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx) 介面指標。|  
  
## 備註  
 如需使用 `CStreamRowset` 中的 `CCommand` 或 `CTable` 宣告，例如:  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/CPP/cstreamrowset-class_1.cpp)]  
  
 或  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/CPP/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` 會傳回 `ISequentialStream` 指標，儲存於 `m_spStream`中。  然後您可以使用 **Read** 方法以擷取 XML 格式的資料 \(Unicode 字串\)。  例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/CPP/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 會執行 XML 格式化，並將資料列集的所有資料行和資料列以 XML 字串傳回。  
  
> [!NOTE]
>  這項功能與僅適用於 SQL Server 2000 搭配使用。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)