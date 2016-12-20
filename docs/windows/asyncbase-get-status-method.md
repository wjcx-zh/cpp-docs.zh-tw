---
title: "AsyncBase::get_Status 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::get_Status"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_Status 方法"
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::get_Status 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取表示非同步作業的狀態的值。  
  
## 語法  
  
```  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
#### 參數  
 `status`  
 要儲存狀態的位置。  如需詳細資訊，請參閱 Windows::Foundation::AsyncStatus 列舉型別。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_ILLEGAL\_METHOD\_CALL。  
  
## 備註  
 這個方法會實作 IAsyncInfo::get\_Status。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)