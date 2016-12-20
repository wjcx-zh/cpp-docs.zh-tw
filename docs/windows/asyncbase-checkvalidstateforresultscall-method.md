---
title: "AsyncBase::CheckValidStateForResultsCall 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForResultsCall 方法"
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::CheckValidStateForResultsCall 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試一個非同步作業的結果是否可以在目前非同步狀態收集。  
  
## 語法  
  
```  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## 傳回值  
 如果結果可以回收即為 S\_OK，否則為 E\_ILLEGAL\_METHOD\_CALLE\_ILLEGAL\_METHOD\_CALL。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)