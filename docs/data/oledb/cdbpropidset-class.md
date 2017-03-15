---
title: "CDBPropIDSet 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropIDSet"
  - "ATL.CDBPropIDSet"
  - "ATL::CDBPropIDSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropIDSet 類別"
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDBPropIDSet 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 **DBPROPIDSET** 結構繼承並將初始化索引鍵欄位以及 [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) 存取方法的建構函式。  
  
## 語法  
  
```  
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|將屬性加入至屬性 ID 集。|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|建構函式。|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|設定屬性 ID 集合的 GUID。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../../data/oledb/cdbpropidset-operator-equal.md)|指定設定的一個屬性 ID 內容到另一個。|  
  
## 備註  
 OLE DB 消費者使用 **DBPROPIDSET** 結構傳遞陣列消費者想要取得屬性資訊的屬性 ID。  在單一 [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 結構識別的屬性所屬的屬性集合。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)