---
title: "AsyncBase::put_Id 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::put_Id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "put_Id 方法"
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::put_Id 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定這個非同步作業的控制代碼。  
  
## 語法  
  
```  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
#### 參數  
 `id`  
 非零的控制代碼。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為 E\_INVALIDARG E\_ILLEGAL\_METHOD\_CALL。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)