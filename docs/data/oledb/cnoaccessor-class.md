---
title: "CNoAccessor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CNoAccessor"
  - "CNoAccessor"
  - "ATL.CNoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoAccessor 類別"
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CNoAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以當做樣板引數 \(`TAccessor`\) 為樣板類別，例如 `CCommand` 和 `CTable`，需要存取子類別引數。  
  
## 語法  
  
```  
class CNoAccessor  
```  
  
## 備註  
 當您不要類別支援參數或輸出資料行時，請使用 `CNoAccessor` 做為樣板引數。  
  
 `CNoAccessor` 會實作下列 Stub 方法，其中每個型別都對應到其他存取子類別方法:  
  
-   **BindColumns** 的屬性存取子的繫結資料行。  
  
-   `BindParameters` \-繫結至資料行的建立參數。  
  
-   **Bind** \-建立繫結。  
  
-   **Close** \-關閉存取子。  
  
-   `ReleaseAccessors` \-版本類別建立存取子。  
  
-   `FreeRecordMemory` \-自由需要釋放在目前資料錄的任何資料列。  
  
-   `GetColumnInfo` \-從開啟資料列集取得資料行資訊。  
  
-   `GetNumAccessors` \-擷取類別建立存取子的數目。  
  
-   `IsAutoAccessor` \-傳回 true，如果資料為存取子自動擷取在移動作業期間。  
  
-   `GetHAccessor` \-擷取指定的存取子存取子的控制代碼。  
  
-   `GetBuffer` \-擷取指標書籤緩衝區。  
  
-   **NoBindOnNullRowset** \-防止在空白資料列集的資料繫結。  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)