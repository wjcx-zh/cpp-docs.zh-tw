---
title: "CDynamicAccessor::GetBookmark | Microsoft Docs"
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
  - "CDynamicAccessor.GetBookmark"
  - "GetBookmark"
  - "CDynamicAccessor::GetBookmark"
  - "ATL.CDynamicAccessor.GetBookmark"
  - "ATL::CDynamicAccessor::GetBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBookmark 方法"
ms.assetid: 6d0a2970-0c62-4a34-bac7-149d8e990f81
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取目前行的書籤。  
  
## 語法  
  
```  
  
      HRESULT GetBookmark(   
   CBookmark< >* pBookmark    
) const throw( );  
```  
  
#### 參數  
 `pBookmark`  
 \[out\] [CBookmark](../../data/oledb/cbookmark-class.md) 物件的指標。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 您必須將 **DBPROP\_IRowsetLocate** 設定為 `VARIANT_TRUE` 以擷取書籤。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)