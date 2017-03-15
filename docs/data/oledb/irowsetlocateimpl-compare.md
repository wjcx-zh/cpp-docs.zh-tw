---
title: "IRowsetLocateImpl::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetLocateImpl.Compare"
  - "IRowsetLocateImpl::Compare"
  - "IRowsetLocateImpl.Compare"
  - "ATL::IRowsetLocateImpl::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare 方法"
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetLocateImpl::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較兩個書籤。  
  
## 語法  
  
```  
  
      STDMETHOD ( Compare )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison   
);  
```  
  
#### 參數  
 請參閱*OLE DB 程式設計人員參考*中的[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)。  
  
## 備註  
 書籤之一可能是標準 OLE DB 定義的 [標準書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx) \(**DBBMK\_FIRST**和 **DBBMK\_LAST**或者 **DBBMK\_INVALID**\)。  在`pComparison` 的值表示傳回兩個書籤之間的關聯性:  
  
-   **DBCOMPARE\_LT** \(`cbBookmark1` 在 `cbBookmark2`之前\)。  
  
-   **DBCOMPARE\_EQ** \(`cbBookmark1` 等於 `cbBookmark2`\)。  
  
-   **DBCOMPARE\_GT** \(`cbBookmark1` 在 `cbBookmark2`之後\)。  
  
-   **DBCOMPARE\_NE** \(書籤相等和未排序\)。  
  
-   **DBCOMPARE\_NOTCOMPARABLE** \(書籤無法比較\)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)