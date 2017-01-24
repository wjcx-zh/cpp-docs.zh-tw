---
title: "RuntimeClass::QueryInterface 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface 方法"
ms.assetid: 8f01f4a1-3fa2-4a8e-88c6-03629236cb9f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::QueryInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取指定介面 ID 的指標。  
  
## 語法  
  
```  
  
STDMETHOD(  
   QueryInterface  
)  
   (REFIID riid,   
   _Deref_out_ void **ppvObject);  
```  
  
#### 參數  
 `riid`  
 介面 ID。  
  
 `ppvObject`  
 當這個作業完成時，由 `riid` 參數指定的介面指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)