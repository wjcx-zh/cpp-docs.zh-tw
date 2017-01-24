---
title: "CRowset::Close | Microsoft Docs"
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
  - "CRowset::Close"
  - "ATL.CRowset.Close"
  - "CRowset<TAccessor>::Close"
  - "CRowset<TAccessor>.Close"
  - "ATL.CRowset<TAccessor>.Close"
  - "ATL::CRowset::Close"
  - "ATL::CRowset<TAccessor>::Close"
  - "CRowset.Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 966d779e-e148-4dc0-bbba-7cfb9fa6a16b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放資料列和目前的 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) 介面。  
  
## 語法  
  
```  
  
void Close( ) throw( );  
  
```  
  
## 備註  
 這個方法目前釋放所有資料列集。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)