---
title: "CDynamicStringAccessorW 類別 | Microsoft Docs"
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
  - "CDynamicStringAccessorW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorW 類別"
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicStringAccessorW 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許可以讓您在不知道資料庫結構描述 \(基礎結構\) 時存取資料來源。  
  
## 語法  
  
```  
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## 備註  
 使用者要求所有資料存放區存取以字串資料的提供者擷取，不過， `CDynamicStringAccessor` 要求 Unicode 字串資料。  
  
 繼承自`CDynamicStringAccessorW` **GetString** 和 `SetString` 從 `CDynamicStringAccessor`。  當您使用時在 `CDynamicStringAccessorW` 的這些方法物件， ***BaseType*** 是 **WCHAR**。  
  
## 需求  
 **標頭** ：atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)