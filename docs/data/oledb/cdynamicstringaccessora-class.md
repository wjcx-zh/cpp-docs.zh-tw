---
title: "CDynamicStringAccessorA 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessorA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorA 類別"
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicStringAccessorA 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您存取資料來源，在不知道資料庫結構描述 \(基礎結構\)。  
  
## 語法  
  
```  
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## 備註  
 使用者要求所有資料存放區存取以字串資料的提供者擷取，不過， `CDynamicStringAccessor` 要求 ANSI 字串資料。  
  
 繼承自`CDynamicStringAccessorA`**GetString** 和 `SetString` 從 `CDynamicStringAccessor`。  當您使用時在 `CDynamicStringAccessorA` 的這些方法物件， ***BaseType*** 是 **CHAR**。  
  
## 需求  
 **Header**:atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)