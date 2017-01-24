---
title: "RuntimeClassBaseT::AsIID 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassBaseT::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### 參數  
 `T`  
 一個實作由參數`riid`所指定的介面 ID的型別。  
  
 `implements`  
 一個由範本參數 `T`所指定型別的變數。  
  
 `riid`  
 要擷取的介面 ID。  
  
 `ppvObject`  
 如果作業成功，由參數 `riid`所指定的對介面之指標的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述錯誤的 HRESULT。  
  
## 備註  
 擷取指定介面 ID 的指標。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)