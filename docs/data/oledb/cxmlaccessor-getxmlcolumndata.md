---
title: "CXMLAccessor::GetXMLColumnData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CXMLAccessor.GetXMLColumnData"
  - "CXMLAccessor::GetXMLColumnData"
  - "CXMLAccessor.GetXMLColumnData"
  - "ATL::CXMLAccessor::GetXMLColumnData"
  - "GetXMLColumnData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLColumnData 方法"
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CXMLAccessor::GetXMLColumnData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由資料列擷取資料表的資料行資訊， XML 格式字串資料。  
  
## 語法  
  
```  
  
      HRESULT GetXMLColumnData(   
   CSimpleStringW& strOutput    
) throw( );  
```  
  
#### 參數  
 `strOutput`  
 \[out\] 包含資料行資訊的字串緩衝區的參考會被擷取。  字串格式化為 XML 符合資料存放區的資料行名稱的標記名稱。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 以下顯示資料行資訊如何在 XML 格式化。  `type` 所指定資料行的資料型別。  請注意資料型別是根據資料庫的 OLE DB 資料型別，而不是存取的項目。  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)