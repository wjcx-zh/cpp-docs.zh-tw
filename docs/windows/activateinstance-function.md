---
title: "ActivateInstance 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Windows::Foundation::ActivateInstance"
  - "client/ABI::Windows::Foundation::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance 函式"
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivateInstance 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註冊和擷取指定的類別 ID 定義的指定型別的執行個體。  
  
## 語法  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### 參數  
 `T`  
 要啟動的型別。  
  
 `activatableClassId`  
 定義參數 `T`的類別識別碼的名稱。  
  
 `instance`  
 這個作業完成時， `T`執行個體的參考。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，指出發生錯誤的原因的錯誤 HRESULT。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Windows::Foundation  
  
## 請參閱  
 [Windows::Foundation 命名空間](../windows/windows-foundation-namespace.md)