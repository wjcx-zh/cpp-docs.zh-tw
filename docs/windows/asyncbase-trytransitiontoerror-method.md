---
title: "AsyncBase::TryTransitionToError 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::TryTransitionToError"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryTransitionToError 方法"
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::TryTransitionToError 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示指定的錯誤碼是否可以修改內部錯誤狀態。  
  
## 語法  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### 參數  
 `error`  
 錯誤的 HRESULT。  
  
## 傳回值  
 `true` ，如果變更內部錯誤狀態;否則， `false`。  
  
## 備註  
 只有在錯誤狀態已經設定為 S\_OK，此作業修改錯誤狀態。  這個作業不會有任何作用，如果錯誤狀態已經是個錯誤，請移除，完成或關閉。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)