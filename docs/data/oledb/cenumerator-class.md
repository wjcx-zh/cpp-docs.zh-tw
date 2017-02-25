---
title: "CEnumerator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CEnumerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumerator 類別"
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CEnumerator 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 OLE DB 列舉程式物件，公開 [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) 介面傳回描述所有資料來源和列舉值的資料列集。  
  
## 語法  
  
```  
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[Find](../../data/oledb/cenumerator-find.md)|查詢會尋找具有指定名稱的可用提供者 \(資料來源\)。|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|擷取目前資料錄的 `IMoniker` 介面。|  
|[開啟](../../data/oledb/cenumerator-open.md)|開啟列舉值。|  
  
## 備註  
 您可以從這個類別間接擷取 **ISourcesRowset** 資料。  
  
## 需求  
 **標頭**：atldbcli.h  
  
## 請參閱  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)