---
title: "CXMLAccessor 類別 | Microsoft Docs"
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
  - "ATL::CXMLAccessor"
  - "CXMLAccessor"
  - "ATL.CXMLAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CXMLAccessor 類別"
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您存取資料來源以字串資料，在不知道資料存放區的結構描述 \(基礎結構\)。  
  
## 語法  
  
```  
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|擷取資料行資訊。|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|由資料列擷取資料表的整個內容。|  
  
## 備註  
 不過， `CXMLAccessor` 與 `CDynamicStringAccessorW` 不同之處在於它轉換從資料存放區存取的所有資料為 XML 格式 \(標記\) 資料。  此為輸出特別有用。XML 明確的 Web 網頁。  XML 標記名稱會盡可能符合資料存放區的資料行名稱。  
  
 使用 `CDynamicAccessor` 方法取得資料行資訊。  您可以在執行階段使用這些資料行資訊，動態地建立存取子。  
  
 資料行資訊是儲存在這個類別所建立和管理的暫存區中。  使用 [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)，取得資料行資訊使用 [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) 或由行衍生資料行。  
  
## 範例  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/CPP/cxmlaccessor-class_1.cpp)]  
  
## 需求  
 **Header**:atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)