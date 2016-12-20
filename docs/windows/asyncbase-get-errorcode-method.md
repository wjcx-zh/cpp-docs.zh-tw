---
title: "AsyncBase::get_ErrorCode 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::get_ErrorCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_ErrorCode 方法"
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::get_ErrorCode 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取目前的非同步作業的錯誤碼。  
  
## 語法  
  
```  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
#### 參數  
 `errorCode`  
 儲存目前的錯誤碼的位置。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_ILLEGAL\_METHOD\_CALL;如果目前非同步作業已關閉。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)