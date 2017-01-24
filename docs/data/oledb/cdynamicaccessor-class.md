---
title: "CDynamicAccessor 類別 | Microsoft Docs"
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
  - "ATL.CDynamicAccessor"
  - "ATL::CDynamicAccessor"
  - "CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor 類別"
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓您能在不知道資料庫結構描述 \(資料庫的基礎結構\) 的情況下，存取資料來源。  
  
## 語法  
  
```  
class CDynamicAccessor : public CAccessorBase  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|覆寫預設存取子時，加入繫結項目至輸出資料行。|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|執行個體化及初始化 `CDynamicAccessor` 物件。|  
|[關閉](../../data/oledb/cdynamicaccessor-close.md)|解除所有資料行的繫結，釋放配置的記憶體，並釋放類別中的 [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) 介面指標。|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|擷取目前行的書籤。|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|擷取目前行的 BLOB 控制碼值。|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|擷取最大的 BLOB 大小 \(以位元組為單位\)。|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|擷取資料列集的資料行數目。|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|擷取資料列的特性。|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|擷取資料行中繼資料。|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|擷取指定資料行的名稱。|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|擷取指定資料行的資料型別。|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|擷取資料行的可能上限 \(以位元組為單位\)。|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|擷取指定資料行名稱的資料行索引。|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|擷取指定資料行的狀態。|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|從緩衝區中擷取資料。|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|設置目前行的 BLOB 控制碼值。|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|設置 BLOB 大小上限 \(以位元組為單位\)。|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|設置資料行的長度 \(以位元組為單位\)。|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|設置指定資料行的狀態。|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|儲存資料至緩衝區。|  
  
## 備註  
 使用 `CDynamicAccessor` 方法取得資料行資訊，例如資料行名稱、資料行計數和資料型別等等。  接下來您可以在執行階段使用這些資料行資訊，動態地建立存取子。  
  
 資料行資訊儲存於這個類別所建立和管理的暫存區中。  使用 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) 方法從緩衝區取得資料。  
  
 如需使用動態存取子類別的詳細資訊和範例，請參閱 [使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。  
  
## 需求  
 **標頭**：atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)