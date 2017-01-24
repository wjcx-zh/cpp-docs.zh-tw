---
title: "CUtlProps::OnPropertyChanged | Microsoft Docs"
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
  - "OnPropertyChanged"
  - "CUtlProps.OnPropertyChanged"
  - "CUtlProps::OnPropertyChanged"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnPropertyChanged 方法"
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::OnPropertyChanged
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會在設定屬性之後的繫結屬性。  
  
## 語法  
  
```  
  
      virtual HRESULT OnPropertyChanged(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### 參數  
 `iCurSet`  
 索引屬性集合陣列中;零，如果只有一個屬性集合。  
  
 `pDBProp`  
 屬性 ID 和新的值在 [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) 結構。  
  
## 傳回值  
 標準 `HRESULT`。  預設傳回值為 `S_OK`。  
  
## 備註  
 如果您要處理繫結的屬性，例如值取決於其他屬性值的書籤或更新，您應該覆寫這個函式。  
  
## 範例  
 在這個函式，使用者從 `DBPROP*` 參數取得屬性 ID。  現在，對屬性比較 ID 與鏈結是可能的。  當找到屬性時， `SetProperties` 會使用與另一個屬性搭配現在要設定的屬性。  在這種情況下，，則會取得 `DBPROP_IRowsetLocate`、 `DBPROP_LITERALBOOKMARKS`或 `DBPROP_ORDEREDBOOKMARKS` 屬性，則可以設定 `DBPROP_BOOKMARKS` 屬性。  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/CPP/cutlprops-onpropertychanged_1.h)]  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)