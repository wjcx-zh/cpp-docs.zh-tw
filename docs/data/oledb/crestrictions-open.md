---
title: "CRestrictions::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRestrictions.Open"
  - "ATL::CRestrictions::Open"
  - "ATL.CRestrictions.Open"
  - "CRestrictions::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRestrictions::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回根據使用者提供的限制設定的結果。  
  
## 語法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true  
);  
```  
  
#### 參數  
 `session`  
 \[in\] 指定使用的現有工作階段物件連接至資料來源。  
  
 *lpszParam*  
 \[in\] 在結構描述資料列集指定限制。  
  
 `bBind`  
 \[in\] 指定是否自動繫結資料行對應。  預設值為 **true**，導致資料行列對應自動繫結。  設定`bBind`為 **false** 以防止資料行列對應的自動繫結，讓您可以手動繫結。\(手動繫結是特殊的感興趣 OLAP 使用者\)。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 在結構描述資料列集可以指定最多七個限制。  
  
 如需每個結構描述資料列集所定義的限制。請參閱 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 。  
  
## 需求  
 **標頭：**atldbsch.h  
  
## 請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)