---
title: "AsyncBase::Close 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::Close 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

結束非同步作業。  
  
## 語法  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## 傳回值  
 S\_OK，如果作業關閉或已已經關閉；否則， E\_ILLEGAL\_STATE\_CHANGE。  
  
## 備註  
 Close\(\) 是 IAsyncInfo::Start 的預設實作，但不會進行實際工作。  若要實際取消非同步作業，請覆寫 OnClose\(\) 純虛擬方法。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)