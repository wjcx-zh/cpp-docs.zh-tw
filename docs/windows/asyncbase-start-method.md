---
title: "AsyncBase::Start 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start 方法"
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::Start 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟動非同步作業。  
  
## 語法  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## 傳回值  
 S\_OK，如果作業開始或已開始；否則， E\_ILLEGAL\_STATE\_CHANGE。  
  
## 備註  
 Start\(\) 是 IAsyncInfo::Start 的預設實作，但不會進行實際工作。  若要實際開始非同步作業，請覆寫 OnStart \(\) 純虛擬方法。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)