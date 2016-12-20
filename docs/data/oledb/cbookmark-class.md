---
title: "CBookmark 類別 | Microsoft Docs"
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
  - "ATL.CBookmark"
  - "ATL::CBookmark<nSize>"
  - "CBookmark"
  - "ATL.CBookmark<nSize>"
  - "ATL::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark 類別"
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示在其緩衝區的書籤值。  
  
## 語法  
  
```  
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase  
template < >  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### 參數  
 `nSize`  
 書籤緩衝區的大小 \(以位元組為單位\)。  當 `nSize` 為零，書籤緩衝區將動態地在執行階段建立的。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|建構函式|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|擷取指標至緩衝區。|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|在位元組擷取緩衝區的大小。|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|將書籤值。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../../data/oledb/cbookmark-operator-equal.md)|指定 `CBookmark` 類別到另一個。|  
  
## 備註  
 **CBookmark\<0\>** 是 `CBookmark`的樣板特製化;其緩衝區動態地在執行階段建立的。  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)