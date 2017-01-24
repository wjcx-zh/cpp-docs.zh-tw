---
title: "IErrorRecordsImpl::GetErrorSource | Microsoft Docs"
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
  - "IErrorRecordsImpl.GetErrorSource"
  - "GetErrorSource"
  - "IErrorRecordsImpl::GetErrorSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorSource 方法"
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorSource
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得導致從錯誤記錄之錯誤的原始程式碼。  
  
## 語法  
  
```  
  
      LPOLESTR GetErrorSource(  
   ERRORINFO& rCurError   
);  
```  
  
#### 參數  
 `rCurError`  
 在 **IErrorInfo** 介面的 `ERRORINFO` 資料錄。  
  
## 傳回值  
 out 包含錯誤之字串的指標原始程式碼。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IErrorRecordsImpl 類別](../../data/oledb/ierrorrecordsimpl-class.md)