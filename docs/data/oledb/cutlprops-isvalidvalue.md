---
title: "CUtlProps::IsValidValue | Microsoft Docs"
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
  - "CUtlProps::IsValidValue"
  - "CUtlProps.IsValidValue"
  - "IsValidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsValidValue 方法"
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::IsValidValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用來在設定屬性之前先驗證值。  
  
## 語法  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### 參數  
 `iCurSet`  
 索引屬性集合陣列中; 如果只有一個屬性集合，則為零。  
  
 `pDBProp`  
 屬性 ID 和新的值在 [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) 結構。  
  
## 傳回值  
 標準版 `HRESULT` 預設回傳值是 `S_OK`。  
  
## 備註  
 如果您在值要執行的任何驗證常式要用來設定屬性，您應該覆寫這個函式。  例如，您可以驗證 **DBPROP\_AUTH\_PASSWORD** 對密碼表判斷有效的值。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)