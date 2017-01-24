---
title: "CXMLAccessor::GetXMLRowData | Microsoft Docs"
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
  - "ATL::CXMLAccessor::GetXMLRowData"
  - "ATL.CXMLAccessor.GetXMLRowData"
  - "CXMLAccessor::GetXMLRowData"
  - "CXMLAccessor.GetXMLRowData"
  - "GetXMLRowData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLRowData 方法"
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor::GetXMLRowData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由資料列擷取資料表的完整內容， XML 格式字串資料。  
  
## 語法  
  
```  
  
      HRESULT GetXMLRowData(   
   CSimpleStringW& strOutput,   
   bool bAppend = false    
) throw( );  
```  
  
#### 參數  
 `strOutput`  
 \[out\] 包含資料表資料的緩衝區的參考會被擷取。  資料已格式化為與 XML 符合資料存放區的資料行名稱的標記名稱的字串。  
  
 *bAppend*  
 \[in\] 指定布林值字串附加到輸出資料流的結尾。  
  
## 傳回值  
 其中一個標準 `HRESULT` 列舉值。  
  
## 備註  
 以下顯示行上資料的 XML 格式。  下面 的`DATA` 表示資料行的資料。  使用移動方法移至所要的資料行。  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)