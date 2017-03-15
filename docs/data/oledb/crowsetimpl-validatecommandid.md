---
title: "CRowsetImpl::ValidateCommandID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl.ValidateCommandID"
  - "CRowsetImpl::ValidateCommandID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ValidateCommandID 方法"
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowsetImpl::ValidateCommandID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會檢查看任一或兩個 **DBID**s 包含字串值，如果是，複製給它的資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## 語法  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 參數  
 `pTableID`  
 \[out 代表資料表 ID. 的 **DBID** 的指標  
  
 `pIndexID`  
 \[out 代表索引 ID. 的 **DBID** 的指標  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 這個方法會將靜態向上轉型由 `CRowsetImpl` 填入其資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  根據預設，這個方法會檢查任一或兩個 **DBID**s 包含字串值，如果是的話，是否複製給它的資料成員。  您可以將這個簽章的方法中的 `CRowsetImpl`衍生類別，則方法將會呼叫而非基底實作。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)