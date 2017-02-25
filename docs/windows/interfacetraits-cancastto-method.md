---
title: "InterfaceTraits::CanCastTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo 方法"
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceTraits::CanCastTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### 參數  
 `ptr`  
 指向型別的指標名稱。  
  
 `riid`  
 `Base`的介面 ID。  
  
 `ppv`  
 如果作業成功， `ppv` 將會指向由 `Base`指定的介面。  否則， `ppv` 將會設為 `nullptr`。  
  
## 傳回值  
 `true` ，如果此作業成功和 `ptr` 轉換至 `Base`的指標；否則， `false` 。  
  
## 備註  
 指示指定的指標是否可轉換成 `Base`的指標。  
  
 如需 `Base`的詳細資訊，請參閱 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)的公用 Typedefs 部分。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)