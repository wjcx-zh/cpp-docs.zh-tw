---
title: "CDBErrorInfo::GetErrorRecords | Microsoft Docs"
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
  - "CDBErrorInfo.GetErrorRecords"
  - "ATL.CDBErrorInfo.GetErrorRecords"
  - "ATL::CDBErrorInfo::GetErrorRecords"
  - "GetErrorRecords"
  - "CDBErrorInfo::GetErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorRecords 方法"
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得指定之物件的錯誤記錄。  
  
## 語法  
  
```  
  
      HRESULT GetErrorRecords(   
   IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords    
) throw( );  
HRESULT GetErrorRecords(   
   ULONG* pcRecords    
) throw( );  
```  
  
#### 參數  
 *pUnk*  
 \[in\] 連結至可以取得錯誤記錄的物件。  
  
 `iid`  
 \[in\] 介面的 IID 與錯誤。  
  
 *pcRecords*  
 \[out\] \(以一為起始\) 計數的指標錯誤記錄。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 使用函式的第一個要檢查衍生錯誤資訊的介面。  否則，請使用第二個表單。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)