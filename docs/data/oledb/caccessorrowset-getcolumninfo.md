---
title: "CAccessorRowset::GetColumnInfo | Microsoft Docs"
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
  - "CAccessorRowset.GetColumnInfo"
  - "CAccessorRowset::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 8ade2388-3c58-43cd-8ed6-499ee0531291
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorRowset::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從開啟資料列集取得資料行資訊。  
  
## 語法  
  
```  
  
      HRESULT GetColumnInfo(  
   DBORDINAL* pulColumns,  
   DBCOLUMNINFO** ppColumnInfo,  
   LPOLESTR* ppStrings   
) const;  
HRESULT GetColumnInfo(  
   DBORDINAL* pColumns,  
   DBCOLUMNINFO** ppColumnInfo   
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 使用者必須釋放傳回的資料行資訊和字串緩衝區。  因此，使用 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 並需要覆寫繫結時，請使用這個方法的第二個版本。  
  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CAccessorRowset 類別](../../data/oledb/caccessorrowset-class.md)