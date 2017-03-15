---
title: "CDataSource::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::GetProperty"
  - "ATL.CDataSource.GetProperty"
  - "CDataSource.GetProperty"
  - "CDataSource::GetProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperty 方法"
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataSource::GetProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回指定之屬性的值已連接資料來源的物件。  
  
## 語法  
  
```  
  
      HRESULT GetProperty(   
   const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant    
) const throw( );  
```  
  
#### 參數  
 `guid`  
 \[in\] 識別屬性的 GUID 設定要傳回屬性。  
  
 `propid`  
 \[in\] 要傳回屬性的屬性 ID。  
  
 *pVariant*  
 \[out\] **GetProperty** 傳回屬性值的 VARIANT 的指標。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 若要取得多個屬性，請使用 [GetProperties](../../data/oledb/cdatasource-getproperties.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)