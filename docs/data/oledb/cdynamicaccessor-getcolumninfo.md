---
title: "CDynamicAccessor::GetColumnInfo | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.GetColumnInfo"
  - "ATL::CDynamicAccessor::GetColumnInfo"
  - "CDynamicAccessor.GetColumnInfo"
  - "CDynamicAccessor::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回大部分消費者所需的資料行中繼資料。  
  
## 語法  
  
```  
  
      HRESULT GetColumnInfo(   
   IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer    
) throw( );  
```  
  
#### 參數  
 `pRowset`  
 \[in\] [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) 介面的指標。  
  
 *pColumns*  
 \[out\] 要在其中傳回資料列集中資料行數目的記憶體指標，這個數目包含書籤資料行 \(如果有的話\)。  
  
 *ppColumnInfo*  
 \[out\] 要在其中傳回 **DBCOLUMNINFO** 結構陣列的記憶體指標。  請參閱 DBCOLUMNINFO 《 *OLE DB 程式設計人員參考》的*[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) 結構」。  
  
 `ppStringsBuffer`  
 \[out\] 記憶體指標，要在其中傳回單一配置區塊內所有字串值 \(*columnid* 或 *pwszName* 內使用的名稱\) 的儲存指標。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 如需資料型別 **DBORDINAL**和 **DBCOLUMNINFO**和 **OLECHAR**的詳細資訊，請參閱《 *OLE DB 程式設計人員參考》的*[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)