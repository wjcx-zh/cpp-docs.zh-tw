---
title: "CRowset::Compare | Microsoft Docs"
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
  - "CRowset<TAccessor>.Compare"
  - "CRowset<TAccessor>::Compare"
  - "ATL.CRowset<TAccessor>.Compare"
  - "ATL::CRowset<TAccessor>::Compare"
  - "CRowset.Compare"
  - "ATL::CRowset::Compare"
  - "ATL.CRowset.Compare"
  - "CRowset::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare 方法"
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) 比較兩個書籤。  
  
## 語法  
  
```  
  
      HRESULT Compare(   
   const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison    
) const throw( );  
```  
  
#### 參數  
 *書籤 1*  
 \[in\] 要比較的第一個書籤。  
  
 *書籤 2*  
 \[in\] 要比較的第二個書籤。  
  
 `pComparison`  
 \[out\] 比較結果之指標。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性 `IRowsetLocate` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetLocate** 到 `VARIANT_TRUE`。  
  
 如需使用對消費者使用書籤的資訊，請參閱 [使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)