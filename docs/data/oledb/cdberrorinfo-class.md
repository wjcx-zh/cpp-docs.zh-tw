---
title: "CDBErrorInfo 類別 | Microsoft Docs"
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
  - "CDBErrorInfo"
  - "ATL::CDBErrorInfo"
  - "ATL.CDBErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBErrorInfo 類別"
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用來處理 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面的 OLE DB 錯誤的支援。  
  
## 語法  
  
```  
class CDBErrorInfo  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|傳回錯誤記錄檔包含所有的錯誤資訊。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|呼叫 [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) 傳回指定之錯誤的基本資訊。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|呼叫 [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) 指標傳回至自訂錯誤物件的介面。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|呼叫傳回 **IErrorInfo** 介面指標的 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) 為指定的資料錄。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|呼叫 [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) 傳回錯誤參數。|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|取得指定之物件的錯誤記錄。|  
  
## 備註  
 這個介面會傳回一個或多個錯誤記錄至使用者。  先呼叫 [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) ，取得計數錯誤記錄。  然後呼叫其中一個存取功能，例如 [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)，來擷取每個資料錄的錯誤資訊。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)