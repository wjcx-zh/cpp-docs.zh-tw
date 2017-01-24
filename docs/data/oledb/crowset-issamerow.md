---
title: "CRowset::IsSameRow | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::IsSameRow"
  - "CRowset.IsSameRow"
  - "IsSameRow"
  - "ATL::CRowset::IsSameRow"
  - "ATL.CRowset.IsSameRow"
  - "CRowset<TAccessor>::IsSameRow"
  - "ATL.CRowset<TAccessor>.IsSameRow"
  - "CRowset<TAccessor>.IsSameRow"
  - "ATL::CRowset<TAccessor>::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow 方法"
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將目前的與指定的資料列相比較。  
  
## 語法  
  
```  
  
      HRESULT IsSameRow(   
   HROW hRow    
) const throw( );  
```  
  
#### 參數  
 `hRow`  
 \[in\] 要比較的資料列之控制代碼與目前資料列。  
  
## 傳回值  
 標準版 `HRESULT` `S_OK` 表示資料列相同。  如需其他值，請參閱 *OLE DB 程式設計人員參考* 上 [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) 中的 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)