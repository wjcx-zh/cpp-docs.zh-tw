---
title: "CDBErrorInfo::GetErrorParameters | Microsoft Docs"
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
  - "ATL.CDBErrorInfo.GetErrorParameters"
  - "CDBErrorInfo::GetErrorParameters"
  - "ATL::CDBErrorInfo::GetErrorParameters"
  - "CDBErrorInfo.GetErrorParameters"
  - "GetErrorParameters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorParameters 方法"
ms.assetid: 3a2dd8e2-fecc-4315-9f2b-ce3138cdd187
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetErrorParameters
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) 傳回錯誤參數。  
  
## 語法  
  
```  
  
      HRESULT GetErrorParameters(   
   ULONG ulRecordNum,   
   DISPPARAMS* pdispparams    
) const throw( );  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考資訊* 中的 [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)