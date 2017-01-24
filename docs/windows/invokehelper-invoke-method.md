---
title: "InvokeHelper::Invoke 方法 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::InvokeHelper::Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Invoke 方法"
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InvokeHelper::Invoke 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
#### 參數  
 `arg1`  
 引數 1。  
  
 `arg2`  
 引數 2。  
  
 `arg3`  
 引數 3。  
  
 `arg4`  
 引數 4。  
  
 `arg5`  
 引數 5。  
  
 `arg6`  
 引數 6。  
  
 `arg7`  
 引數 7。  
  
 `arg8`  
 引數 8。  
  
 `arg9`  
 引數 9。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述錯誤的 HRESULT。  
  
## 備註  
 呼叫其簽章包含指定數目引數的事件處理常式。  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [InvokeHelper 結構](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)