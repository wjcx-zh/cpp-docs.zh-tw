---
title: "AsyncBase::Cancel 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::Cancel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Cancel 方法"
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::Cancel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消非同步的作業。  
  
## 語法  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## 傳回值  
 根據預設，一律會傳回 S\_OK。  
  
## 備註  
 Cancel\(\) 是 IAsyncInfo::Cancel 的預設實作，但未進行實際工作。  若要實際取消非同步作業，請覆寫 OnCancel\(\) 純虛擬方法。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)