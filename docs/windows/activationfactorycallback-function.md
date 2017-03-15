---
title: "ActivationFactoryCallback 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::ActivationFactoryCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactoryCallback 函式"
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActivationFactoryCallback 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### 參數  
 `activationId`  
 指定的執行階段類別名稱的字串的控制代碼。  
  
 `ppFactory`  
 這個作業完成時，對應至參數 `activationId`的啟用處理站。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述失敗的 HRESULT。  可能的失敗 HRESULT 是 CLASS\_E\_CLASSNOTAVAILABLE 和 E\_INVALIDARG 。  
  
## 備註  
 取得指定之啟動 ID的啟用 Factory  
  
 在Windows執行階段呼叫這個回呼函式所需的執行階段類別名稱指定的物件。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)