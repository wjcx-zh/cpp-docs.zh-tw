---
title: "GetActivationFactory 函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::GetActivationFactory"
  - "client/ABI::Windows::Foundation::GetActivationFactory"
  - "client/Windows::Foundation::GetActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActivationFactory 函式"
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetActivationFactory 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取範本參數指定之型別的啟動 Factory。  
  
## 語法  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### 參數  
 `T`  
 指定啟動 Factory 型別的樣板參數。  
  
 `activatableClassId`  
 啟動 Factory 可以產生類別的名稱。  
  
 `factory`  
 這個作業完成時，會啟動 Factory 的參考型別 `T`。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，錯誤 HRESULT 表示此作業失敗的原因。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Windows::Foundation  
  
## 請參閱  
 [Windows::Foundation 命名空間](../windows/windows-foundation-namespace.md)