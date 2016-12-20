---
title: "IRowsetUpdateImpl::IsUpdateAllowed | Microsoft Docs"
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
  - "IRowsetUpdateImpl::IsUpdateAllowed"
  - "IRowsetUpdateImpl.IsUpdateAllowed"
  - "IsUpdateAllowed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsUpdateAllowed 方法"
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::IsUpdateAllowed
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

覆寫這個方法會檢查安全性，完整性等，在更新之前發生。  
  
## 語法  
  
```  
  
      HRESULT IsUpdateAllowed(  
   DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */  
);  
```  
  
#### 參數  
 *status*  
 \[暫止的作業已在執行中。  
  
 *hRowUpdate*  
 \[為使用者要更新的資料列中處理。  
  
 *pRowStatus*  
 \[狀態傳回給使用者。  
  
## 備註  
 如果您判斷應該允許更新，則傳回 `S_OK`;否則傳回 **E\_FAIL**。  如果您允許使用者更新，您也需要在 [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) 的 **DBROWSTATUS** 到適當的 [資料列狀態。](https://msdn.microsoft.com/en-us/library/ms722752.aspx)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)