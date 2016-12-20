---
title: "CSimpleRow::Compare | Microsoft Docs"
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
  - "CSimpleRow.Compare"
  - "CSimpleRow::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare 方法"
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較兩個資料列，以查看它們是否參考相同的資料列執行個體。  
  
## 語法  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
```  
  
#### 參數  
 `pRow`  
 `CSimpleRow` 物件的指標。  
  
## 傳回值  
 `HRESULT` 值，通常是 `S_OK`，表示兩個是相同的執行個體，或者 **S\_FALSE**，表示兩個資料行是不同的。  如需其他可能的傳回值，請參閱《 *OLE DB 程式設計人員參考》的*[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) 。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)