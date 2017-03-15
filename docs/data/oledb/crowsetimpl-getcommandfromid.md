---
title: "CRowsetImpl::GetCommandFromID | Microsoft Docs"
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
  - "CRowsetImpl::GetCommandFromID"
  - "GetCommandFromID"
  - "CRowsetImpl.GetCommandFromID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCommandFromID 方法"
ms.assetid: 9f39cb07-1c40-486f-ba5b-cb4a65fab8a7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::GetCommandFromID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檢查任一或兩個參數是否包含字串值，如果是，複製字串值給資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## 語法  
  
```  
  
      HRESULT CRowsetBaseImpl::GetCommandFromID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 參數  
 `pTableID`  
 \[in\] 表示表單 ID. 的 **DBID** 的指標  
  
 `pIndexID`  
 \[in\] 表示索引 ID. 的 **DBID** 的指標  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法會將靜態向上轉型由 `CRowsetImpl` 填入資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  根據預設，這個方法會檢查任一或兩個參數是否包含字串值。  如果它們包含字串值，這個方法會複製至資料成員的字串值。  您可以將這個簽章的方法中的 `CRowsetImpl`衍生類別，則方法將會呼叫而非基底實作。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)