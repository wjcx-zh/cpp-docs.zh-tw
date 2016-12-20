---
title: "IErrorRecordsImpl::GetBasicErrorInfo | Microsoft Docs"
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
  - "ATL::IErrorRecordsImpl::GetBasicErrorInfo"
  - "IErrorRecordsImpl::GetBasicErrorInfo"
  - "GetBasicErrorInfo"
  - "ATL.IErrorRecordsImpl.GetBasicErrorInfo"
  - "IErrorRecordsImpl.GetBasicErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBasicErrorInfo 方法"
ms.assetid: d0b4dec3-f32a-4aaa-8365-524f2e7c8395
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetBasicErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回有關錯誤的基本資訊，例如傳回碼和提供者特定的錯誤代碼。  
  
## 語法  
  
```  
  
      STDMETHOD( GetBasicErrorInfo )(  
   ULONG ulRecordNum,  
   ERRORINFO *pErrorInfo   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IErrorRecordsImpl 類別](../../data/oledb/ierrorrecordsimpl-class.md)