---
title: "CDBErrorInfo::GetErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetErrorInfo"
  - "ATL.CDBErrorInfo.GetErrorInfo"
  - "CDBErrorInfo.GetErrorInfo"
  - "ATL::CDBErrorInfo::GetErrorInfo"
  - "CDBErrorInfo::GetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorInfo 方法"
ms.assetid: 234e1f02-c307-4666-b3ce-2a4d62407fa1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫會傳回 [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面指標的 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) 為指定的資料錄。  
  
## 語法  
  
```  
  
      HRESULT GetErrorInfo(   
   ULONG ulRecordNum,   
   LCID lcid,   
   IErrorInfo** ppErrorInfo    
) const throw( );  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考資訊* 中的 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)