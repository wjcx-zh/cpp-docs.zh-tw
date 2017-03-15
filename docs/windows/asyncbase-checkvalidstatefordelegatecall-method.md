---
title: "AsyncBase::CheckValidStateForDelegateCall 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForDelegateCall 方法"
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::CheckValidStateForDelegateCall 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試委派屬性是否在目前非同步狀態進行修改。  
  
## 語法  
  
```  
inline HRESULT CheckValidStateForDelegateCall();  
```  
  
## 傳回值  
 S\_OK，如果委派是可以修改的屬性;否則， E\_ILLEGAL\_METHOD\_CALL。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)