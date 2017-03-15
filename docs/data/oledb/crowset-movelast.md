---
title: "CRowset::MoveLast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset<TAccessor>::MoveLast"
  - "CRowset<TAccessor>::MoveLast"
  - "ATL.CRowset.MoveLast"
  - "ATL::CRowset::MoveLast"
  - "CRowset<TAccessor>.MoveLast"
  - "MoveLast"
  - "CRowset::MoveLast"
  - "ATL.CRowset<TAccessor>.MoveLast"
  - "CRowset.MoveLast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveLast 方法"
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::MoveLast
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將游標移至最後一行。  
  
## 語法  
  
```  
  
HRESULT MoveLast( ) throw( );  
  
```  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 呼叫 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) 變更位置之公司擷取位置到最後一個位置並擷取最後一行。  
  
 這個方法需要將 **DBPROP\_CANSCROLLBACKWARDS** 對 `VARIANT_TRUE` 在呼叫中包含資料列集的資料表的 **Open** 或命令。\(如需更好的效能，您也可以設定 **DBPROP\_QUICKRESTART** 為 `VARIANT_TRUE`\)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)