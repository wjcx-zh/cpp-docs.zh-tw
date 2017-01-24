---
title: "CRowsetImpl::GetColumnInfo | Microsoft Docs"
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
  - "GetColumnInfo"
  - "CRowsetImpl.GetColumnInfo"
  - "CRowsetImpl::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取特定用戶端要求的行資訊。  
  
## 語法  
  
```  
  
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(  
   T* pv,  
   ULONG* pcCols   
);  
```  
  
#### 參數  
 `pv`  
 \[in\] 對使用者的 `CRowsetImpl` 衍生類別的指標。  
  
 `pcCols`  
 \[in\] 指標 \(輸出\) 的資料行數目。  
  
## 傳回值  
 對靜態 **ATLCOLUMNINFO** 結構的指標。  
  
## 備註  
 這個方法是高階覆寫。  
  
 這個方法由數個基底實作類別呼叫擷取特定用戶端要求的行資訊。  通常，這個方法要由 `IColumnsInfoImpl`呼叫。  如果您覆寫這個方法，則 `CRowsetImpl`必須置於方法衍生類別版本。  由於方法在非樣板化類別可能位置，您必須將 `pv` 變更為適當的 `CRowsetImpl`衍生類別。  
  
 下列範例示範 **GetColumnInfo's** 用法。  在此範例中，是 **CMyRowset** `CRowsetImpl`衍生類別。  若要覆寫這個類別的所有執行個體的 `GetColumnInfo` ，將下列方法在 **CMyRowset** 類別定義:  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/CPP/crowsetimpl-getcolumninfo_1.h)]  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)