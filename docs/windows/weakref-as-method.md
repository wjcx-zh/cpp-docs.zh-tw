---
title: "WeakRef::As 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::As"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "As 方法"
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::As 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定指定的 ComPtr 指標參數代表指定的介面。  
  
## 語法  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### 參數  
 `U`  
 介面識別碼。  
  
 `ptr`  
 這項作業完成時，表示參數 `U` 的物件。  
  
## 傳回值  
  
-   如果作業成功，為 S\_OK；否則為表示作業失敗原因的 HRESULT，且 `ptr` 設為 `nullptr`。  
  
-   如果作業成功，為 S\_OK，但已釋放目前的 WeakRef 物件。 參數 `ptr` 設定為 `nullptr`。  
  
-   如果作業成功，為 S\_OK，但目前的 WeakRef 物件不是衍生自參數 `U`。 參數 `ptr` 設定為 `nullptr`。  
  
## 備註  
 如果參數 `U` 是 IWeakReference，或不衍生自 IInspectable，就會發出錯誤。  
  
 第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C\+\+ 語言功能的協助程式特製化，例如[auto](../cpp/auto-cpp.md) 類型推斷關鍵字。  
  
 從 Windows 10 SDK 開始，如果無法取得弱式參考，這個方法不會將 WeakRef 執行個體設定為 `nullptr`，因此您應該避免檢查錯誤的程式碼，檢查 WeakRef 有沒有 `nullptr`。 相反地，請檢查傳回的 HRESULT，以判斷此方法是否成功，或檢查 `ptr` 是否有 `nullptr`。  
  
## 需求  
 **標頭：**client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [WeakRef 類別](../windows/weakref-class.md)