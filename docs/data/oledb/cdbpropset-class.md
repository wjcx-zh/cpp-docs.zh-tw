---
title: "CDBPropSet 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropSet"
  - "ATL.CDBPropSet"
  - "ATL::CDBPropSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropSet 類別"
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CDBPropSet 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 **DBPROPIDSET** 結構繼承並將初始化索引鍵欄位以及 `AddProperty` 存取方法的建構函式。  
  
## 語法  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|將屬性加入至屬性集。|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|建構函式。|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|設定 **DBPROPSET** 結構的 **guidPropertySet** 欄位。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../../data/oledb/cdbpropset-operator-equal.md)|指定設定的一個屬性集內容到另一個。|  
  
## 備註  
 OLE DB 提供者和消費者使用 **DBPROPSET** 結構傳遞 `DBPROP` 結構的陣列。  每個 `DBPROP` 結構表示可以設定的單一屬性。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET Structure](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)