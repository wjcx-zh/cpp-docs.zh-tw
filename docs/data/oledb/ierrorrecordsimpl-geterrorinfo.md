---
title: "IErrorRecordsImpl::GetErrorInfo | Microsoft Docs"
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
  - "GetErrorInfo"
  - "IErrorRecordsImpl.GetErrorInfo"
  - "IErrorRecordsImpl::GetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorInfo 方法"
ms.assetid: 44d0872f-f25f-4102-8f7f-a2cfb3eeb1a0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的紀錄上傳回 [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面指標。  
  
## 語法  
  
```  
  
      STDMETHOD( GetErrorInfo )(  
   ULONG ulRecordNum,  
   LCID lcid,  
   IErrorInfo **ppErrorInfo   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考資訊* 中的 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IErrorRecordsImpl 類別](../../data/oledb/ierrorrecordsimpl-class.md)