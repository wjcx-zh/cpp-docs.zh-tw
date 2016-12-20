---
title: "AsyncBase::get_Id 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::get_Id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_Id 方法"
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::get_Id 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取這個非同步作業的控制代碼。  
  
## 語法  
  
```  
STDMETHOD(  
   get_Id  
)(unsigned int *id) override;  
```  
  
#### 參數  
 `id`  
 要儲存的控制代碼的位置。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_ILLEGAL\_METHOD\_CALL。  
  
## 備註  
 這個方法會實作 IAsyncInfo::get\_Id。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)