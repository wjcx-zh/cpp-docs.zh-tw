---
title: "RuntimeClassBaseT::GetImplementedIIDS 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetImplementedIIDS 方法"
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassBaseT::GetImplementedIIDS 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### 參數  
 `T`  
 `implements` 參數的型別。  
  
 `implements`  
 指向參數 `T`所指定型別的指標。  
  
 `iidCount`  
 介面 ID 要擷取的最大項目數。  
  
 `iids`  
 如果這個作業成功完成，介面 ID 的陣列是由型別 `T`實作。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述錯誤的 HRESULT。  
  
## 備註  
 擷取由指定型別所實作的介面 ID 的陣列。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)