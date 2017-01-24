---
title: "CRowset::MoveNext | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>.MoveNext"
  - "ATL.CRowset.MoveNext"
  - "ATL::CRowset<TAccessor>::MoveNext"
  - "CRowset<TAccessor>.MoveNext"
  - "CRowset.MoveNext"
  - "CRowset<TAccessor>::MoveNext"
  - "CRowset::MoveNext"
  - "ATL::CRowset::MoveNext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveNext 方法"
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveNext
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將游標移至下一個記錄。  
  
## 語法  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### 參數  
 `lSkip`  
 \[in\] 擷取之前所略過的資料列數。  
  
 `bForward`  
 \[in\] 傳遞 **true** 以移至下一個資料錄，傳遞 **false** 以往回移動。  
  
## 傳回值  
 標準版 `HRESULT` 當資料列集的結尾已經到達時，傳回 **DB\_S\_ENDOFROWSET**。  
  
## 備註  
 擷取 `CRowset` 物件的下一個連續行，記住上一個位置。  或者，您也可以選擇略過並往前 `lSkip` 行或往回。  
  
 這個方法需要在呼叫資料表中的**Open**或包含資料列集的命令前，設定下列屬性：  
  
-   如果 `lSkip` \< 為 0，**DBPROP\_CANSCROLLBACKWARDS** 必須為 `VARIANT_TRUE`  
  
-   假如 `bForward` \= false，**DBPROP\_CANFETCHBACKWARDS** 必須為 `VARIANT_TRUE`  
  
 否則 \(如果`lSkip` \> \= 0且 `bForward` \= true\)，就不需要設定任何其他屬性。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)