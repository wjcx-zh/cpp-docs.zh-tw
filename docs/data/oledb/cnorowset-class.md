---
title: "CNoRowset 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CNoRowset"
  - "ATL::CNoRowset<TAccessor>"
  - "CNoRowset"
  - "ATL.CNoRowset<TAccessor>"
  - "ATL::CNoRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoRowset 類別"
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CNoRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以當做樣板引數 \(`TRowset`\) 為 [CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md)。  
  
## 語法  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別  預設為 `CAccessorBase`。  
  
## 備註  
 如果命令不傳回資料列集，請使用 `CNoRowset` 做為樣板引數。  
  
 `CNoRowset` 會實作下列 Stub 方法，其中每個型別都對應到其他存取子類別方法:  
  
-   **BindFinished** \-指示，當繫結完成 \(傳回 `S_OK`\)。  
  
-   **Close** \- 釋放資料列和目前的 IRowset 介面。  
  
-   `GetIID` \-擷取連接點的介面 ID。  
  
-   **GetInterface** \-擷取介面。  
  
-   `GetInterfacePtr`傳回封裝的介面指標。  
  
-   **SetAccessor** \-將存取子的指標。  
  
-   **SetupOptionalRowsetInterfaces** \-設定資料列集的選擇性介面。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)